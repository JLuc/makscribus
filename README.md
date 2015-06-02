makscribus
==========
Scripts which update, make and install bleeding-edge Scribus svn versions and provide various features.
Current scripts are _maksvn_ and _makgit_.  
  
#### Currently tested runs on:
<!-- [ ] Ubuntu 14.10 -->
- [x] Ubuntu 14.04
- [x] Ubuntu 13.10

The folder structure that the scripts uses :

|Directory |Reason  |
| :-------- | :----- |
| ~/dev/scribus/build/subfolder | for build files |
| ~/bin/subfolder               | for results of compile |
| ~/dev/scribus/svn or git      | for source files |

### maksvn

Using Subversion: update to trunk svn head and make scribus 1.5

Default folder structure is :

|Directory |Reason |
| :-------- | :----- |
| ~/bin/scribus15svn        | for results of compile  |
| ~/dev/scribus/build/15svn | for build files         |
| ~/dev/scribus/svn         | for svn source files    |
| ~/dev/scribus             | as main working directory and place for .diff |

Folders can be changed in editing the settings inside the file at its begining.

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
* sourcepath=~/dev/scribus
* qtpath="/localbin/Qt5.4/5.4"
* execdirpath=/localbin
* makeexecname="scribus-1.5.0" # Once was scribus-1.5.0.svn but changed due to 1.5 approaching release. Might be edited for 1.5.1svn
* mylang="fr;en-us" # EDIT to fit your langage !!
* cores=8 # fit your cpu cores = possible parallel processes
* suffix=15svn # postfix for executable. For example : when suffix is 15svn, executable will be scribus15svn
* ```revision="" 					# for latest svn
  revision=19507 				# to "update" to said revision``` 
Uncomment and edit to compile an old revision or to not update OR use the -r 19232 option in the command line
* revision="nomaj" or "noup" 	# so as to prevent update
* usercmakeopt=" -DWANT_DEBUG=1 " # More options for cmake. Do include the -
* usermakeopt="" # More options for make. Do include the -

### ~~makgit~~
_out of order due to lack of activity on the contributor's repo_

Using Git: update to some branch of the contributors GIT repo's head and make scribus 1.5 version for that branch 

Folder structure is the same with name of leaf folder depending on git branch

# Todo

* option to make 1.5.0 released version without having to mention the revision number

Maybe :
* preliminary checks to see if svn + gcc + cmake etc packages are installed
* add il8n functionality (translate the script prompts to other languages) [[Discussion]](https://github.com/JLuc/makscribus/issues/2)
* use getopts to parse CLI options

Other script :
* install libraries and svn + compilers when required
* required ? offer other linux 'flavor' options...(involves mostly fine-tuning library installs)
* checkout and update plugin from github and compile ? (for ex https://github.com/aoloe/scribus-plugin-export-epub)

