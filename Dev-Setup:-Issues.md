## Under Construction

If you get errors with bower not being able to clone git repositories, try [cloning over https](http://stackoverflow.com/questions/1722807/git-convert-git-urls-to-http-urls/11383587#11383587).  If SASS brings up an error about file encodings being wrong, add this to your .bash_profile:
```bash
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
```
If you only see a white screen, check to see if the first line of app.css is `ERROR: Cannot load compass`. If so, try either uninstalling compass (`gem uninstall compass`) or re-installing it if you actually need it (`gem install compass --pre`).

**Note**: if your brunch isn't compiling sass properly (`public\stylesheets\app.css` is like 70KB instead of >600KB and you get a white screen on http://localhost:3000 with no JavaScript errors), try removing the bless-brunch entry from package.json and deleting the bless-brunch folder from node_modules. Also make sure you have the latest sass gem. If you rebrunch, it may work.
