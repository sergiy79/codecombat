###Index:
* [Simple Linux](#simplelinux)

### <a name="simplelinux"></a> Simple Linux

On Linux, you'll need make, build-essential, ruby, curl and git installed (`sudo apt-get install make build-essential ruby curl git`).

1. [Create a GitHub account](https://github.com/join) if you don't already have one.
2. [Set up Git on your computer](https://help.github.com/articles/set-up-git/) to allow your computer to speak to GitHub
3. (Optional) [Fork](https://github.com/codecombat/codecombat/fork) our CodeCombat repository if you wish to make changes.
4. Make sure
5. Open a terminal and navigate to the folder you wish to install CodeCombat under.
6. * If you've forked the repository, paste in the following command.  *Replace "your_repository_url" with your repository*.

    ```bash
    curl https://raw.githubusercontent.com/codecombat/codecombat/master/scripts/devSetup/bootstrap.sh | bash -s your_repository_url
    ```
   * If you haven't forked the repository, paste in the following command.
    ```bash
    curl https://raw.githubusercontent.com/codecombat/codecombat/master/scripts/devSetup/bootstrap.sh | bash
    ```
    NOTE: The repository will be in the coco subdirectory.  You should not run a separate git clone, as that is taken care of.
7. Ensure you have Python 2 installed with `sudo apt-get install python2`, or your distributional equivalent.  Python 3.1 is also supported, but 3.2+ are not tested.
8. Follow the on-screen prompts.  The program will download and install all necessary dependencies.  If nothing seems to be happening, try running `sudo python ./coco/scripts/devSetup/setup.py` or join the [HipChat](www.hipchat.com/g3plnOKqa) to fix things.
9.  Run the following commands in separate windows:
    * `./coco/bin/coco-mongodb` - Starts MongoDB
    * `sudo ./coco/bin/coco-brunch` - Starts brunch, which watches for file changes 
    * `./coco/bin/coco-dev-server` - Starts your local web server
10. Setup [MongoDB](#MongoDB) *Soon to be Optional*
### To be Edited
11. Visit [http://localhost:3000](http://localhost:3000) to see your CodeCombat development environment!

If you get errors with bower not being able to clone git repositories, try [cloning over https](http://stackoverflow.com/questions/1722807/git-convert-git-urls-to-http-urls/11383587#11383587).  If SASS brings up an error about file encodings being wrong, add this to your .bash_profile:
```bash
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
```
If you see a white screen only, check to see if the first line of app.css is `ERROR: Cannot load compass.`. If so, try either uninstalling compass (`gem uninstall compass`) or re-installing it if you actually need it (`gem install compass --pre`).
