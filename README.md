# wildfire
Experiment to visualise a tinderbox document on a webpage using reactjs.

## Setup notes

1. update npm, on OSX this is: sudo npm install npm@latest -g
   c.f. https://docs.npmjs.com/getting-started/installing-node

2. install / update nvm: curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash
   restart the terminal after this (or follow the hints near the end of the install message)

3. install node: nvm install node

4. install the create-react-app: npm install create-react-app

5. create and clone a repo. Assuming you have initialised a repo on github,
   clone with, e.g.: git clone https://github.com/mrkeir/wildfire.git

6. inside the repo, i.e. *cd wildfire*  use the create-reach-app command to
   create a new react app. e.g. create-react-app wf-app

   Note: I had some trouble with permissions here, likely some oddness from
   having an ancient version of nodejs on the system before.  The fix for me
   was to clear the npm cache as root, one time: sudo npm cache clean

7. after creating the new react app, expect to see a message like:

---

```Success! Created wf-app at /Users/keirr/Documents/wildfire/wf-app
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd wf-app
  npm start
```
---

And check that you can start the development server.

8. check in the files, but first create a .gitignore file to ignore the
   node_modules cruft.

   base1:wildfire keirr$ cat .gitignore
   node_modules/

   git add .gitignore README.md wf-app
