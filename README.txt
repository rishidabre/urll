README
------

Starting with the ability of launching a given URL in a browser instantly
from our smartphone, the URLL (URL Listener) utility now provides a few more
actions like lock, unlock user session and even shutdown the machine. Owing to
its extended capabilities and a potential to offer even more, it can very well
be called as 'Use Right Love Linux'.

Primarily, URLL allows you to instantly open URLs from your Android smartphone
on a Linux system on the same LAN. We use the NetTools app on Android as
'netcat' to connect to and send messages on a predefined port of the Linux
machine. Just as the URL sent from the phone is received by the system, a
browser window pops open and you can enjoy a full size view of the same page.

This is the basic version of URLL and does not employ any kinds of security
measures or restrictions. Further, the end sending URLs could very well be
another Linux system or a system having the 'netcat' capability. Consequently,
you may use any other suitable app of your choice for this purpose.

This file contains the necessary information for setting up and using the
'urll' module. For detailed technical information, please refer
'technical_notes.txt'.

Requirements
------------
1. On Linux system
   - bash 4.3.48(1)-release (x86_64-pc-linux-gnu)
   - socat 1.7.3.1
   - mawk 1.3.3
   - google-chrome 60.0.3112.113
2. On Android device
   - NetTools - Network Essentials v1.1.0 by AG Applications
     (available on Play Store)

Setup
-----
1. On Linux system
   - Extract the contents in source in a local directory, call it, URLL home
   - Run the 'setup' file as follows:
     ./setup <path_to_urll_home>
     (Note: You will need to be a sudoer for this.)
   - Reboot the machine
2. On Android device
   - Download the NetTools app from the Play Store (link below):
     https://play.google.com/store/apps/details?id=atg.andr.nettools&hl=en
   - Stay in the Netcat menu, enter the host name of Linux machine and the port
     number as previously configured (keep 'Listen' unchecked)

Directions
----------
1. Launch a URL
   - Hit 'Start' in the NetTools app, enter the URL and hit enter, your page
     should be already up on screen! :)
2. Perform new actions
   - These actions can be performed by following the steps from 1 above and
     sending instead of a URL, the following commands-
     i. lock : to lock the current user session
     ii. unlock : to unlock the current user session
     iii. shutdown : to shutdown the machine
3. Stop URLL
   - Go to the URLL home directory and run './stop_urll'
4. Revert changes from 'setup'
   - From the URLL home directory, run './revert'

Limitations
-----------
1. URLs are not validated before passing through to browser.
2. Device authentication is not supported.

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

5. setup
   - This file creates a script named init_urll.sh under /etc/profile.d which
     takes care of starting URLL after user logs in.

6. revert
   - This file does the exact opposite of 'setup' i. e. revert rc.local to its
     previous state.

Issues
------
1. Currently, using commands 'lock' and 'unlock' evokes an issue related to
   user sessions in Ubuntu 16.04 LTS. This causes a user to, after previously
   having used above commands, see the error message 'Authentication failure'
   on the greeter screen when they manually lock their session. As per the
   discussion on the relevant thread, upgrading to 17.10 solves the issue (but
   we have not tested it).
   Link to bug: https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1733557

-------------------
Author- Rishi Dabre
