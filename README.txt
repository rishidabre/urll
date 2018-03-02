README
------

URLL (URL Listener) allows you to instantly open URLs from your Android
smartphone on a Linux system on the same LAN. We use the NetTools app on Android
as 'netcat' to connect to and send messages on a predefined port of the Linux
machine. Just as the URL sent from the phone is received by the system, a
browser window pops open and you can enjoy a full size view of the same page.

This is the basic version of URLL and does not employ any kinds of security
measures or restrictions. Further, the end sending URLs could very well be
another Linux system or a system having the 'netcat' capability. Consequently,
you may use any other suitable app of your choice for this purpose.

This file contains the necessary information for setting up and using the 'urll'
module.

Requirements
------------
1. On Linux system
   - socat 1.7.3.1
   - mawk 1.3.3
   - google-chrome 60.0.3112.113
2. On Android device
   - NetTools - Network Essentials v1.1.0 by AG Applications
     (available on Play Store)

Setup
-----
1. Extract the main directory contents in a local directory
2. Add (and modify accordingly) the following two lines at the end of your local
   '.bashrc' file
      export URLL_HOME=/path/to/local/directory
      $URLL_HOME/start_urll

Limitations
-----------
1. Since the URL listener starts through the .bashrc program, a terminal window
   needs to be open in order for the connection to establish.
2. URLs are not validated before passing through to browser.

Files
-----
1. url_listener
   - The main file responsible for creating a 'socat' endpoint for listening
     to any incoming URLs.
   - Here, you can change the port number (1230 ?) for incoming connections to
     whatever you like.

2. url_launcher
   - Responsible for launching the supplied URL in google-chrome in incognito
     mode.
   - Here, you may comment the 'google-chrome' line and uncomment the 'firefox'
     line should you like to use the latter.

3. start_urll
   - Starts the urll module.

4. stop_urll
   - Stops the urll module.

-------------------
Author- Rishi Dabre
