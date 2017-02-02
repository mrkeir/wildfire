.. _Tinderbox: http://www.eastgate.com/Tinderbox/
.. _ReactJS: https://facebook.github.io/react/
.. _Wildfire: https://github.com/mrkeir/wildfire

========
Wildfire
========

  Experiment to visualise a Tinderbox_ document on a webpage using ReactJS_.

Setup notes
-----------

1. update npm, on OSX this is::

    sudo npm install npm@latest -g

  cf. [https://docs.npmjs.com/getting-started/installing-node]

2. install / update nvm::

    curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash

    restart the terminal after this (or follow the hints near the end of the install message)

3. install node: nvm install node

4. install the create-react-app: npm install create-react-app

5. create and clone a repo. Assuming you have initialised a repo on github,
   clone with, e.g.::

    git clone https://github.com/mrkeir/wildfire.git

6. inside the repo, i.e. *cd wildfire*  use the create-reach-app command to
   create a new react app. e.g.::

      create-react-app wf-app

   Note: I had some trouble with permissions here, likely some oddness from
     having an ancient version of nodejs on the system before.  The fix for me
     was to clear the npm cache as root, one time::

       sudo npm cache clean

7. after creating the new react app, expect to see a message like::

      Success! Created wf-app at /Users/keirr/Documents/wildfire/wf-app
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

   And check that you can start the development server with `npm start`


8. check in the files, but first create a .gitignore file to ignore the node_modules cruft::

    base1:wildfire keirr$ cat .gitignore
    node_modules/

    git add .gitignore README.md wf-app

9. get the reactjs devtools for Chrome. Debugging on Chrome is likely to be
   less hassle than Safari, or the browser formerly known as IE.
   Get the React Development Tools extension on the Chrome web store.

   Once the devtools are installed you can inspect the running app in the usual
   way (Cmd-alt-I on a Mac, or by mouse abuse), and find a new React tab at
   the end of the menu that start Elements Console...


The Big Idea
------------

Tinderbox_ is built around the concept of a note - which has content, attributes,
and links to other notes.  Notes may be nested. Notes can appear in more than
one place as aliases (similar to symlinks on a Unix filesystem).
Notes can also be active (agents) and templates (prototypes), but for this
project I want to visualise the content of a Tinderbox_ document on a webpage,
not recreate the application in its entirety.

Tinderbox_ provides an export feature for which one can define export templates
to control the output. Tinderbox_ saves its documents in XML, although I'm not
aware of any public definition of the structure.

I considered using the XML as the input into Wildfire_, but the advantages
of using an export template are compelling. Much of the complexity of Tinderbox_
can be removed with an export template, saving early versions of Wildfire_ from
having to deal with (i.e. ignore) advanced Tinderbox_ features.


The First Step
--------------

I'll need a Tinderbox_ document, starting with one note. Then create an export
template to render JSON for that note. Tinderbox_ notes have a host of
properties, but for now I'll simple export the name (title) and text (content).
