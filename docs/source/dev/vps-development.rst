Development Using the Virtual Private Server
=================

Developing Using the VPS
-----------------
* Development of the Backend of the app will entail the tasks
    - They will have to write some code, compile it, scp it to the VPS, test it. This will also mean that there will be periods of time where the API is unavailable to front end developers as it's being used for backend development.

* **Do not attempt steps on this page if you do not feel confident doing so. Speak to Thomas and he can provide guidance.**

SSH
-----------------
* The VPS does not have a desktop environment, it can only be accessed through a CLI environment. For Windows users, this will probably be Command Prompt or Powershell; Mac users will use Terminal; and Linux users must find a suitable terminal. (it has been tested to work with Alacritty).

* Login using the setap account (details provided the Google Doc) so your SSH will look something like this

    - $ ssh [ACCOUNT_NAME]@[SERVER_IP_ADDRESS]
    - You may be prompted if you want to continue connecting as the authenticity of the host cannot be established. Type yes to continue.

* Then you will be prompted for the password - enter this and press enter. If you are copy-pasting, note that ctrl + v (or cmd + v for Apple users) will not work.
    - Permitting everything has worked, you should then be in a SSH session with the VPS.

SCP
-----------------
* The VPS does not have FTP ports opened. This means that you will need to get friendly with SCP to be able to move files to the VPS.

* SCP is a command line application, the syntax to copy a file called movemeplease.txt from a documents folder on Linux to the home folder on the VPS.

    - $ scp /Documents/movemeplease.txt setap@[SERVER_IP_ADDRESS]:~
    - It will then behave like SSH in that it will ask you for a password for the user account. A more general SCP syntax can be seen below:

    - $ scp [path-to-file-or-folder-to-copy] [username]@[ip-of-machine-to-copy-to]:[path-to-destination]

**Running The File**

* The file needs to be moved into the /usr/bin directory and be called ecotrackr-api. Don't worry about overwriting the old file (in theory we can recompile to this from Git Commits if we get desperate).

* Then restart the service running on the VPS with the command sudo systemctl restart ecotrackr-api and finally check that it is running with the command sudo systemctl status ecotrackr-api (it should say its running at this stage).

    - *Any issues - give Thomas a shout.*