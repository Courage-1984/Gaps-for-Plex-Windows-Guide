# Gaps for Plex Windows Guide
Gaps for Plex Windows Guide. 
**Find the missing movies in your Plex Server!**

Find Gaps here: https://github.com/JasonHHouse/gaps


## What you need to download:

1. Download the latest release of Gaps on Windows, found on the [releases page](https://github.com/JasonHHouse/gaps/releases) (Download the `GapsAsJar-0.10.4.zip` file).
2. Download the Windows YML file (`application-windows.yaml`) found [here](https://github.com/JasonHHouse/gaps/blob/master/GapsWeb/src/main/resources/application-windows.yaml).  **OR** right click > save as [this link](https://github.com/JasonHHouse/gaps/blob/master/GapsWeb/src/main/resources/application-windows.yaml).
3. Download `OpenJDK 11.0.2 (build 11.0.2+9)` found [here](https://jdk.java.net/archive/) (Download the `Windows 64-bit` **zip** file).  **OR** click [here](https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_windows-x64_bin.zip).

Gaps and the YML file will be stored in this repo as well for archival purposes. So alternatively you can download them in [this folder](https://github.com/Courage-1984/Gaps-for-Plex-Windows-Guide/tree/main/Gaps%20and%20Windows%20YML%20file) by right clicking the file > save as.


## Where to put the downloaded files:

1. Unzip the `GapsAsJar-0.10.4.zip` folder and place it somewhere like inside of `C:\Program Files\Gaps` (so you should now have `C:\Program Files\Gaps\GapsAsJar` with files inside that).
2. Place the `application-windows.yaml` file inside the `GapsAsJar` folder (not sure if this file is necessary but it says so in the og wiki).
3. In the root of you `C:` drive create a folder called `usr`, inside that create a folder called `data` and inside that create a file called `gaps.properties`.

(`.properties` is the file extension, just create a new text document and name it `gaps.properties` instead of `New Text Document.txt`)

You should now have `C:\usr\data\gaps.properties`.

4. Unzip the `openjdk-11.0.2_windows-x64_bin.zip` folder and place it somewhere like inside of `C:\Program Files\jdk11` (so you should now have `C:\Program Files\jdk11\jdk-11.0.2` with files and folders inside that).


## Some file editing that needs to be done:

*we will treat the `jdk 11` as portable so no installation or changing of path variables or environmental variables is needed.*

1. Navigate to your `GapsAsJar` folder created in the previous step 1.
2. Open `startOnWindows.bat` with a code editor or a text editor.
3. Replace the 4 instances of `call java -jar` with:

```bat
  call "C:\Program Files\jdk11\jdk-11.0.2\bin\java" -jar
```

This should be the path if you followed the previous step 4 to the letter, otherwise replace the path in qoutations with the path you created.

4. Save the `startOnWindows.bat` file and close your editor.


## How to run:

1. Inside your `GapsAsJar` folder, click the address bar and enter `cmd`.
2. A CLI should pop up and in which you enter `startOnWindows.bat`.
3. Give it a sec to start and run, after which you navigate to the following url in your browser:
```sh
  http://localhost:8484/
```


## TMDB and Plex setup:

**TMDB** (www.themoviedb.org):

1. Navigate to the following link: https://www.themoviedb.org/settings/api
2. Create an account if necessary.
3. Get a developer API key, fill in the needed form.
4. Navigate to the following link: https://www.themoviedb.org/settings/api
5. Your **API Key** should be displayed there.
6. With **Gaps** open in your browser, click the `Settings` tab > `TMDB` option and fill in your `Movie Database Api Key`.
7. Click Test.
8. If successful click Save.


**Plex** :

1. With **Gaps** open in your browser, click the `Settings` tab > `Plex` option.
2. Fill in your `Plex IP Address` which is usually `localhost` or `127.0.0.1`.
3. Fill in your `Plex Port` which is usually `32400`.
4. Fill in your `Plex Token`, to find your `Plex Token` do the following:
5. Open `Plex Web App` in your browser, login if needed, navigate to any movie, click the three dots > click `Get info`, click on `View XML` at the bottom of the modal popup.
6. In the new page that opens, click on the address bar and at the end of the address you should find `X-Plex-Token=YOUR_TOKEN`.
7. Copy everything after `X-Plex-Token=` and paste it into your `Plex Token` field in Gaps.
8. Click Test.
9. If successful click Save.


## Next Steps:

1. With Gaps open in your browser click the `Libraries` tab.
2. Click the dropdown button and select your Plex `Movies` library.
3. Click the Search button to find your Plex Movies. **GIVE GAPS TIME TO COMPLETE THIS SEARCH**

Gaps will display the movies found in the Plex Server Library.

*Note: Rerun this step for each server you want Gaps to find the missing movies in.*

4. Scroll to the bottom of the page and check the `entries` amount if it matches your Plex Movie library amount (It might be very slightly off due to movies that it did not find matches for).
5. When this search is done continue:
6. With Gaps open in your browser click the `Missing` tab.
7. Click the dropdown button and select your Plex `Movies` library.
8. Click the Search button to find your missing movies. **GIVE GAPS TIME TO COMPLETE THIS SEARCH** (you can check your open terminal if it's still busy).

*note:* **For large libraries, this can take a while to run. The results are stored and only need to be rerun when Plex updates. Missing movies are added as found. Do not navigate away. Gaps will still run, but you'll have to check logs to know when it is complete. It is currently easier to just leave the page open**


## EXTRA:

**You change the `Show missing movies` setting in the Settings tab > TMDB, to set if you want `All` or `Released`.**

Further settings can be customised in the `Settings` tab of Gaps.


## Debug:

**You might need to rerun Gaps:**

In your terminal where you ran `startOnWindows.bat`, press `Ctrl+C` to stop `Gaps` or close the CLI.

Navigate back to https://github.com/Courage-1984/Gaps-for-Plex-Windows-Guide?tab=readme-ov-file#how-to-run and follow steps.


## Important:

- View https://github.com/JasonHHouse/gaps for `Gaps` general information and setup.
- View https://github.com/JasonHHouse/gaps/wiki/Windows for the `Windows Wiki` for `Gaps`.
- View https://support.plex.tv/articles/204059436-finding-an-authentication-token-x-plex-token/ for `Finding an authentication token / X-Plex-Token` - a `Plex` article (this didn't help me tbh).


## SOURCES:

*some sources that helped me with getting Gaps to work:*

- [Gaps on Windows : "Could not save your Plex configuration" #308](https://github.com/JasonHHouse/gaps/issues/308)
- [Plex connects but won’t add. #289](https://github.com/JasonHHouse/gaps/issues/289)


# DONE!

**Enjoy Gaps!**

