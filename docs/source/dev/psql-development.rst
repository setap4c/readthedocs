PostgreSQL Configuration
=================

Logging in through the VPS
-----------------
* To login to the interactive PSQL shell, run the psql command and it will launch the shell. This works for the setap user.

* For the root user of the VPS - first switch user to the postgres user.

Additional Users
-----------------
* *It is obviously a bad idea to use the Postgres user for everything so an additional user has been created for use in the Dart code. This also has superuser access as this is easiest for while we are testing things.*

* Details are in the VPS Information sheet in the Google Shared Drive.

Interacting with PostgreSQL through Dart
------------------
* There is a postgres package which makes communication really easy. There is also an example on the GitHub (add link here) of how this works.