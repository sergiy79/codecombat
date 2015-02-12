### Adding Sample Code to your Level

This is the default code shown in the editor where the player types code while playing. When teaching a new concept, the sample code can be a complete solution to the level, with a few key lines left to the player. A practice level might only include a few comments with hints.

To add sample code:

1. Edit the "Hero Placeholder" thang (double click on it in the level editor).
1. Look for the programming.Programmable Component.
1. Fill in the following properties:

- **programmableMethods**
  - **plan:**
    - **languages:** This is where you put sample source for languages other than Javascript. It's a good idea to include Python, at least.
    - **name:** "plan"
    - **source:** This is where your sample Javascript source code goes.
    - **Comments:** this is a list of strings used to display comment text in your sample code. Put the actual text of your comment here, such as `attack_ogre`: `"Attack the ogre!"`, then in your sample code you include this comment with: `// <%= attack_ogre %>`. Using these Comments: properties (instead of hard-coding comments in the samples) makes translation into different languages easier.
