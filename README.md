# txclipsvc
A simple clipboard text service(both server and client side code) written in Golang and supports Windows, Linux and Mac OS.

# Install

First, you need a server with one public IP(which could be accessed via Internet), and better have the adminitrator/root privilege of the server.

In windows, run the following command in the CMD console with administrator privilege,
> txclipsvc install

In Linux & Mac systems, run the following command in the console/terminal,
> sudo txclipsvc install

Then the clipboard service should be running on the default port 7458.

# Uninstall

> txclipsvc uninstall

# Run directly(not as service)

run the app with any arguments will cause it running in command mode(not service mode):

> txclipsvc version
