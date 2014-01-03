From the beginning, we knew we wanted to make CodeCombat into a multiplayer programming game. When you're coding by yourself, not only is it not as fun, but it's much easier to get stuck--and whether you're a beginner or not, nothing is more frustrating than spending an hour debugging something that could have been fixed in five seconds by another pair of eyes. Beginners aren't going to get better at programming by doing that--they're going to give up and think programming isn't for them. But if there's another Wizard in there, then not only is it much harder for both players to get stuck at the same time, but you can also do much harder and more interesting challenges. And wouldn't it be awesome to go head-to-head in real time against your friends and random foes on the internet?

CodeCombat's multiplayer collaborative code editing is done. It uses [Firepad in the spell editor](https://github.com/codecombat/codecombat/wiki/Tome#multiplayer-and-firepad), which adds operational transform support to ACE. We turn it on when a player enables multiplayer in their session from the Multiplayer button at the top, after which they can just send their multiplayer link to anyone to join.

![Preliminary multiplayer game list](https://dl.dropboxusercontent.com/u/138899/GitHub%20Wikis/multiplayer_00.png)

Top improvements would include:

* Multiplayer games list. You'd have to implement things like letting players choose how many others they wanted in their game. Actually, we have a game list right now that's admin-only because it doesn't have these player controls; as soon as we have that kind of public filtering, we can unlock that.
* Syncing script state across players. We have a plan for how to do this, but it'll be a bit complicated to get right.
* Head-to-head play. It's kind of set up to allow players to control different teams, but there's no interface for choosing wizard's teams, and there's no team-based victory conditions. We were thinking a competitive mechanism whereby you have to hold the advantage for five minutes to win, and whenever the winning teams switch based on code improvements one player makes, their timer starts counting up instead. There are many ways to go about this.
* Co-op missions with different teams controlled by different players. So one player might have to write the code for a hero, and the other might have to write the code for the minions, and only when both players solved their part could they triumph.
* Call for help. We have a ton of Ambassador volunteers signed up ready to jump into beginner's games and help them out when they get stuck, so whenever we build the "I'm stuck, please send an experienced Wizard to my aid!" button, we can get an awesome mentor/mentee thing going on, perhaps even with social ratings and points for helping other players.