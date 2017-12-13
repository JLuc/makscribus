Linux scripts which update, make, compiles and install bleeding-edge Scribus svn versions and provide various features.
Current script list is :
- _maksvn_ 
- _makgit_ (not maintened).  

#### Preliminary notice
No bad issue has ever been reported so far with these scripts but they sure can be improved. 
- The author or the scribus team are NOT responsible for your computer crash or data loss. 
- Use this at your own risk.
- Pull requests are wellcome !

#### prereqisites

The dev version of all required libs has to be installed first

This might possibily do it :
``` 
sudo apt install build-essential cmake gettext libboost-python-dev libcairo2-dev libcdr-dev libcups2-dev libfreehand-dev libgraphicsmagick++1-dev libharfbuzz-dev libhunspell-dev libhyphen-dev libicu-dev liblcms2-dev libmspub-dev libopenscenegraph-dev libpagemaker-dev libpodofo-dev libpoppler-cpp-dev libpoppler-dev libpoppler-private-dev libqt5opengl5-dev libqt5webkit5-dev librevenge-dev libtiff-dev libvisio-dev libwpg-dev libxml2-dev python-all qtbase5-dev qttools5-dev qttools5-dev-tools zlib1g-dev
```
(thanks ale)

# maksvn

Using Subversion: update to trunk svn head or to any other revision, and make scribus 1.5.2 or 'preBoxes' version.

Folders can be changed in editing the settings inside the file at its begining.
- path to Qt
- path for exec
- etc

#### Currently tested runs on:
- [x] Ubuntu 14.04 (tested by JLuc, Dec2016)
- [x] Ubuntu 13.10 (tested by JLuc, Dec 2013)
- [x] slackware 14.1 (tested by John Culleton, Dec 2015)

#### Basic use

Plain `maksvn` updates the source to svn head (currently 1.5.1svn), compiles and installs it

#### Options
Various options enhances the use. the options order is important.

```maksvn [-h]ou[-?] [diff [dest]] [-d]ou[clean] [-r #####] [-nomaj]```

* -h or -? display this help
* -diff or diff : creates the diff file 'dest.diff' (or 'svnhead.diff' when no dest filename is specified) of the current files state, when they have been localy edited, agains the svn head.
* -d or clean : Deletes previous build files (not the execs)
* -r ##### : updates to old revision n°#####  (default : update to head)
* -noup or -nomaj : dont update at all, but make and install

#### Settings

Other settings require to edit the file and change their default values.

You MUST have a look at them and change their value before launching the script, or create the folder structure according to them.

Here are their name and défault values :
* `sourcepath=~/dev/scribus`
* `qtpath="/localbin/Qt5.4/5.4"`
* `execdirpath=/localbin`
* `makeexecname="scribus-1.5.0"` : Once was scribus-1.5.0.svn but changed due to 1.5 approaching release. Might be edited for 1.5.1svn
* `mylang="fr;en-us"` : Edit to fit your langage !!
* `cores=8` : edit to fit your cpu cores = compile is much quicker with parallel processes enabled
* `suffix=15svn` : postfix for executable. For example : when postfix is 15svn, executable will be scribus15svn
* `revision` setting sets the default revision for update and can be overwriten with command line option
  - `revision=""` : to update to latest svn
  - `revision=19507` : to "update" to said revision``` 
  - `revision="nomaj"` or `"noup"`  : no update at all, will compile source "as is" 
* `usercmakeopt=" -DWANT_DEBUG=1 "` : More optionnal settings for cmake. Do include the -
* `usermakeopt=""` : More optionnal settings for make. Do include the -


|Directory use  | default value | setting variable name |
| :-------- | :----- | :----- |
| main working directory and place for .diff files | ~/dev/scribus             | sourcepath |
| svn source files    | ~/dev/scribus/svn          | $sourcepath/svn |
| build files     |  ~/dev/scribus/15svn | $sourcepath/build/$suffix |
| for results of compile |  /localbin/15svn | $execdirpath/$suffix |
| path for Qt | /localbin/Qt5.4/5.4 |  $qtpath |

When the script is launched, it creates the scribus related folders in case they dont exist, but not the qtpath : Qt has to be installed first, and the script checks it is installed in the said place.

### ~~makgit~~
_out of order due to lack of activity on the contributor's repo_

Using Git: update to some branch of the contributors GIT repo's head and make scribus 1.5 version for that branch 

Folder structure is the same with name of leaf folder depending on git branch

# Todo

* DONE option to make 1.5.0 released version without having to mention the revision number

Maybe :
* preliminary checks to see if svn + gcc + cmake etc packages are installed
* add il8n functionality (translate the script prompts to other languages) [[Discussion]](https://github.com/JLuc/makscribus/issues/2)
* use getopts to parse CLI options

Other script :
* install libraries and svn + compilers when required
* required ? offer other linux 'flavor' options...(involves mostly fine-tuning library installs)
* checkout and update plugin from github and compile ? (for ex https://github.com/aoloe/scribus-plugin-export-epub)

Main repo : https://github.com/JLuc/makscribus/
