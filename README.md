# txclipsvc
A simple clipboard text service(both server and client side code) written in Golang and supports Windows, Linux and Mac OS.

# Install

There is only one executable file for txClipSvc. It can run as a stand-alone server(or system service if you wish), as well as the client-side application. For client side, download the released zip file here, extract it to any directory, and it's ready to use then. For server side installation, please see the instructions below.

First, you need a Windows/Linux/MacOS server with at least one public IP(which could be accessed via Internet), and better have the adminitrator/root privilege of the server.

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

# Customization/Configuration

## Default base directory
Default base directory is used to store config file for the server, log file for both server and client, and the clip text temporary file for the client.

In windows, the default base directory is c:\txclipsvc. In Linux and Mac, the default base directory is /txclipsvc. You can change the base directory by adding command-line parameter "-base=YOUR_PATH", but it only works on client side or command mode(or manually starting mode). Since the service automatically run by the system would run without any parameters, so it could not be changed. If you have no root privilege, the best choice is run the app in manually mode in background but not autostart service mode, then you can specify base directory other than the default. For example,

> txclipsvc -base=/Users/abc/txclipsvc

## The files in the base directory
There should be 3 files in the base directory(make sure you have write-access to the directory),
- txclipsvc.cfg
  You can store various parameters to control the server-side behaviour.
- txclipsvc.log
  Application logs while running in service mode.
- clip.txt
  The real text content for the clipboard cache.

## Edit the config file to run server with custom port
Add a line of text in the config file(i.e. txclipsvc.cfg), the restart the service(use the command-line: txclipsvc reinstall), and the service will run on the specified port.
> port=8083

# Client side guide
To use the service, you should first edit the config file in the base directory first, if there is not, create one manually. Sample content of config file in client side is shown as below,

> server=clip.youdomain.com
> code=test
> port=7458

## To save/set some text on the server-side

> txclipsvc set -text="This is a pie."
This will set the text for the code/user "test" in server-side.

or if you don't specify any text in the command-line, and use the specified code,

> txclipsvc save -code=myself
This will set the text from clipboard for the code/user "myself" in server-side.

or you can set it get the text from the cache file in the base directory,
> txclipsvc save -file
This will set the text from clipboard for the code/user "myself" in server-side.

## To get saved text from server-side

> txclipsvc get
The stored text in the server-side will be retrieved to the local clipboard, the cache file, and the standard ouput.

or

> txclipsvc get -code="common"
Retrieve the text for the specified code/user.

# Other comments

- The maximum number of codes/users is set to 100, and the maximum text size to 8000 charactres now.
- Any comments or suggestions, please send e-mail to topget@163.com .
