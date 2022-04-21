# bibliotecaortodoxa-cartile
basic flutter app: file copy&app_launcher

# TL;DR
Create an open source app that should copy its assets folder files to phone's storage and do an url launch or app launch. Keep it simple and reuse existing packages. Priority Android.

# Details and the flow:

1. A simple (naive) test should be done if the files were already copied and provide an option to recopy or skip it. (e.g. for test: have a file in our app's private storage (or in a config in sqlplus) if the copy was done previously for this release).


2. (depending on 1), the app should copy the files (forcefully, non-interactive) from its assets directory to the external storage under Books folder, maintaining the directory structure. Copy progress should be shown (a simple counter would also do: file <x> out of <...>). If there was an error, print a message the user with a "mailto:" to a...@gmail.com.
(In the assets folder there will be the contents of this zip: https://drive.google.com/file/d/1g0kvPgzIr1VXcwNaIgFsgRkar9j7pgkg/view)
(see shared_storage package)

3. The app has to check if an epub handler exists (see url_launcher package)

4. If it does, it should call the current handler for epub files for the "intro.epub" from the Books folder.
If no such handler exists, it should try to open the FBReader App (on Android): either the app will open or the Goole Playstore should open for the FBReader app (see external_app_launcher package).
On IOS the behaviour should be similar to the extend is possible (worst case scenario it should open the Market place for an epub reader able to read from external storage).
  
# Guidelines & Notes:
  
0. Every time the app decides it has to copy or access the files to external storage it'll check if it has the perms and if they are missing we'll have to prompt the user for it.

1. The app should base as much as possible on existing plugins.
Plugins which you may want to use for copying to external storage:
https://pub.dev/packages/shared_storage

2. Plugins which you may want to use for lauching the epub handler or the app or playstore:
https://pub.dev/packages/url_launcher
https://pub.dev/packages/external_app_launcher

3. Other links of interest:
https://github.com/GeekyAnts/external_app_launcher/issues/4
https://github.com/JideGuru/FlutterEbookApp

4. The app should work on Android and IOS, with priority and full functionality expected for Android (11+).

# Next
In the future (not part of this effort), a search box should be added to select the desired book and call the url_launcher for it.
For indexing the metadata of the books, epubx package should be used. Suggestions should be enabled.
Integrate OS's search so the books can be found and launched from there as well.
