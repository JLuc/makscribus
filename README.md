makscribus
==========

Scripts to make and install scribus.
Folder structure is
~/bin/subfolder : for results of compile
~/dev/scribus/build/subfolder : for build files
~/dev/scribus/svn or git : for source files

* maksvn : update to trunk svn head and make scribus 1.5

Works on Ubuntu 13.10

Folder structure is :
~/bin/scribus15svn        for results of compile
~/dev/scribus/build/15svn for build files
~/dev/scribus/svn         for svn source files
~/dev/scribus             as main working directory and place for .diff

* makgit : update to some branch of the contributors GIT repo's head and make scribus 1.5 version for that branch - out of order due to lack of activity on the contributor's repo

Folder structure is the same with name of leaf folder depending on git branch

Todo
----

* add il8n functionality (translate the script prompts to other languages) [[Discussion]](https://github.com/JLuc/makscribus/issues/2)
* offer other linux 'flavor' options...(involves mostly fine-tuning library installs)
* preliminary checks to see if svn + gcc + cmake etc packages are installed
* install libraries and svn + compilers when required
* init the svn checkout
* Ability to specify target directories instead of pre-determined ones
