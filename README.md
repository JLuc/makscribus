makscribus
==========
Scripts which make and install Bleeding-Edge Scribus versions.  
Current scripts are _maksvn_ and _makgit_.  
  
#### Currently runs on:
<!-- [ ] Ubuntu 14.10 -->
- [ ] Ubuntu 14.04
- [x] Ubuntu 13.10


The folder structure that the scripts use:

|Directory |Reason  |
| :-------- | :----- |
| ~/dev/scribus/build/subfolder | for build files |
| ~/bin/subfolder               | for results of compile |
| ~/dev/scribus/svn or git      | for source files |

### maksvn

Using Subversion: update to trunk svn head and make scribus 1.5

Folder structure is :

|Directory |Reason |
| :-------- | :----- |
| ~/bin/scribus15svn        | for results of compile  |
| ~/dev/scribus/build/15svn | for build files         |
| ~/dev/scribus/svn         | for svn source files    |
| ~/dev/scribus             | as main working directory and place for .diff |

### ~~makgit~~
_out of order due to lack of activity on the contributor's repo_

Using Git: update to some branch of the contributors GIT repo's head and make scribus 1.5 version for that branch 

Folder structure is the same with name of leaf folder depending on git branch

# Todo

Improve :
* command line options instead of EDIT inline values for revision number option*
* use getopts to parse CLI options

Maybe :
* preliminary checks to see if svn + gcc + cmake etc packages are installed
* add il8n functionality (translate the script prompts to other languages) [[Discussion]](https://github.com/JLuc/makscribus/issues/2)

Other script :
* install libraries and svn + compilers when required
* required ? offer other linux 'flavor' options...(involves mostly fine-tuning library installs)
* checkout and update plugin from github and compile ? (for ex https://github.com/aoloe/scribus-plugin-export-epub)

Out of scope :
* Ability to specify target directories instead of pre-determined ones

Done june 2014 :
* inline parameters for produced bin UI lang and nb of CPU cores compile
* force ~/dev/scribus as initial folder for sources and build, create it when needed
* init the svn checkout
* English spoken

