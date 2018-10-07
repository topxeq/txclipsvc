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

# Run directly/manually(not as service)

Run the app with any arguments will cause it running in command mode(not service mode):

> txclipsvc version

Especially, you can manually run the app without any arguments to force it running as a service. This is useful for the situation that you could not get the administrator/root privilege on the server.

# Default base directory

Default base directory is used to store config file for the server, log file for both server and client, and the clip text temporary file for the client.

In windows, the default base directory is c:\txclipsvc. In Linux and Mac, the default base directory is /txclipsvc. You can change the base directory by adding command-line parameter "-base=YOUR_PATH", but it only works on client side or command mode(or manually starting mode). Since the service automatically run by the system would run without any parameters, so it could not be changed. If you have no root privilege, the best choice is run the app in manually mode in background but not autostart service mode, then you can specify base directory other than the default. For example,

> txclipsvc -base=/Users/abc/txclipsvc

# Run the server with custom port

> txclipsvc -port=
