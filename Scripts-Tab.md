On the scripts tab, add new scripts on the left and configure them on the right. Here are some key properties in Scripts:

* **ID**: A name for you to refer to the script by, and for other scripts to refer to it (if you want to make sure that one script only happens after another script)
* **Event**: The type of message that will happen to trigger this script, like when the world is built (ie, when the code has been evaluated). Right now there’s an autocomplete of the ones we ourselves have used so far.
* **Event Checks**: Logical tests. So for example, the “surface:frame-changed” event might be too broad, so you have an event check which says only if the frame is greater than 30 does the script fire.
* **Actions**: List of things that happen when the script is triggered. The properties in here are fairly well documented if you explore them (remember, selecting a row in a Treema will tell you more about the property generally). Actions are organized in ‘note groups’, which happen sequentially (when you press ‘enter’, the current note group ends and the next one begins).

Scripts and Components are the most black-magic part of this editor. Our best advice is to check out our existing levels and see what they do in these areas and mimic them. If you can’t find how to do something, find us in our [public HipChat room](http://www.hipchat.com/g3plnOKqa) and we’ll help you out.

### Example

Say you want your level to start paused. You would create a script with event ‘god:new-world-created’ and then create a single note group in the actions. That note group then sets playback.playing to false. The ‘god:new-world-created’ event happens whenever the level is constructed from the current code, which happens once all the resources have been loaded, so tying a script to it also works as an ‘initialize’ script.

### Configuring Victory/Defeat Conditions

For plan()-based levels, by default the level ends in defeat 5 seconds after a Programmable Plans Thang has finished all its plans. To adjust this, edit each such Thang’s Plans configuration to set its worldEndsAfter config to either null (to make the world not end because of this) or another number.

All other win/loss conditions so far are based on Goals added with Scripts. By default, new levels created now have win-after-three-seconds-if-all-ogres-die and lose-after-three-seconds-if-all-humans-die goals. These are also hidden, in that they don’t show up in the “Objectives” area unless they’re failed. These are pretty good for last-thang-standing humans vs. ogres levels, but not for other setups, for which you’d want to configure/remove these. They’re in the “Add Default Goals” script.

Say you wanted the level to end in success if 1) you grabbed at least 3 of the 5 potions, 2) you had 3 humans survive, 3) Tharin must survive, 4) you killed all the ogres, and 5) at least 3 humans exited the left side of the level. You want the level to end 4 seconds after you know you’ve either lost or won. You’d set up these goals:

* “Grab three potions” - Collect
    * How Many: 3
    * Who: [“humans”]
    * Targets: [“Potion”, “Potion1”, “Potion2”, “Potion3”, “Potion4”]
    * World Ends After: 4
* “Save three soldiers” - Save Thangs
    * How Many: 3
    * Who: [“humans”]
    * World Ends After: 4
* “Tharin must survive” - Save Thangs
    * Who: [“Tharin”]
    * World Ends After: 4
* “Defeat the ogres” - Kill Thangs
    * Who: [“ogres”]
    * World Ends After: 4
* “Escape to the east” - Leave Off Sides
    * How Many: 3
    * Who: [“humans”]
    * Sides: [“right”]
    * World Ends After: 4