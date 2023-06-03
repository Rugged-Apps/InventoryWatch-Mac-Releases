# InventoryWatch-Mac-Releases
Repo to serve InventoryWatch macOS app updates 

# Update Process
_Note: If all else fails, just follow this Sparkle guide: https://troz.net/post/2023/sparkle/_

1. Make any/all necessary changes to the app, bump the version/build number, and commit to `main` (if necessary)
2. Archive the build, notarize (via Xcode), and export the notarized build
3. Open the [DMG Canvas](https://www.araelium.com/dmgcanvas) project, point the InventoryWatch build contents to the build you just exported
4. Build the DMG, and then move it to the `./Releases` folder. Be sure to move the prior version to the `./Archive` folder (with a filename like this `<VERSION>_<BUILD>_InventoryWatch.dmg`)
5. Regenerate the `./Releases/appcast.xml` file by running Sparkle's `generate_appcast` script. To find this script, you can open Xcode, show the Sparkle package in Finder, and find the script like this, and run it.

```
// From Xcode's Sparkle path, navigate to the script
$ cd ../../artifacts/sparkle/Sparkle/bin/

// Run the script
$ ./generate_appcast /path/to/your/Releases/folder
```

7. `appcast.xml` should be updated; add any release notes to the latest `item` in the file with this format:

```xml
<description><![CDATA[
    <h2>What's New</h2>
    <ul>
        <li>Add</li>
        <li>Entries</li>
        <li>Like</li>
        <li>This</li>
    </ul>
]]>
</description>
```

8. Commit these changes to this repo's `main` branch, and push
9. Open `InventoryWatch.app`, check for updates, and verify your update appears!
