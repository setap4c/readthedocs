Setup Guide
=============

* The EcoTrackr app is built using the Dart language for logic with the support of the flutter framework as a UI toolkit. Therefore it is necessary that Dart and Flutter are installed on the system that will be running this application.
* It is reccomended to have an emulator that allows the simulation of mobile devices however this is not necessary and this application can simply be run on the web.

1. Using git, clone the repository into your desired workspace, ensuring that you are able to access the contents of the folder. The repository can be cloned using either the CLI or GitHub Desktop.
2. Once the repository has been cloned, open it in your prefered IDE (Such as VSCode or IntelliJ Idea), Ensuring that the working directory is the same as the directory the project was cloned into.
3. Install Dependancies by running *'flutter pub get'* in the terminal, This will install all required dependancies otherwise stated in the **'pubspec.yaml'** file. Flutter will download all the necessary files into the *'lib'* folder.
4. Configuring devices can be done by either connecting a physical device, emulating a device or by simply running the applciation through the web. 
    - *in the event that web support is not enabled, Run 'flutter config --enable-web' in the terminal*
5. Executing **'flutter run'** from the root directory. This command will present options of your selected emulators, select prefered choice and the application will begin running.
6. Stopping the application can be done by simply pressing down the *control* button and *c* at the same time in the terminal. **(ctrl + c)**

* The application requires no running of the backend services as these have already been initialized and setup to run full-time during the duration of this project.
* Documentation on how this was set up can be found here: :ref:`../dev/index`
