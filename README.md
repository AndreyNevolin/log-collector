#Log Collector

## Description
A simple tool that allows collecting - in a single console - text messages
sent from different applications/shell consoles.
The messages can be printed in different colours.

![Log Collector example](/example.png?raw=true "Log Collector at work")

The tool consists of three components:

1. 'Log server' - a very short Python script (file ```log_server```) that
	brings up a simple HTTP server. The server listens for incoming
	text messages and sends them to a console which it was started from
2. 'Log client' - also a very short Python script (file ```log_client```)
	that can be used to send messages to the server
3. A configuration file (```log_server.cfg```) used by the server and the
	client to understand what port and IP address the server should be
	sitting on.
	The contents of the file is very simple. E.g:
	
	```
	[common]
	server_ip=127.0.0.1
	server_port=8000
	```

## How to use
1. Python 3 is required to run the scripts
2. Put ```log_server``` and ```log_client``` to ```/usr/local/bin```
3. Put ```log_server.cfg``` to ```/etc``` (also you may edit this file if
	required)
4. Start the server in a separate console: just type ```log_server``` (or
	```python3 /usr/local/bin/log_server```, depending on how you access
	Python 3.x interpreter)
5. Send message to the server from a different console:
	```log_client colour message_to_print```
	(or ```python3 /usr/local/bin/log_client colour message_to_print```
	depending on your environment)
	
	```colour``` here is a name of the colour you want to print the message in
	
	```message_to_print``` is the message you want to print

Currently only ```default, blue, cyan, green```, and ```red``` colours are
supported. But adding other colours is straightforward.

To see coloured messages you should start ```log_server``` in a shell that
supports colours. Otherwise ```colour``` information will be ignored.

## License
Copyright © 2017 Andrey Nevolin, https://github.com/AndreyNevolin
 * Twitter: @Andrey_Nevolin
 * LinkedIn: https://www.linkedin.com/in/andrey-nevolin-76387328
  
This software is provided under the Apache 2.0 Software license provided in
the [LICENSE.md](LICENSE.md) file
