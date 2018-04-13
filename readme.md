# Configure

## Purpose

This script will permit to generate and configure makefile easily, with dialog box or config file, for C or C++ projects.

## Usage

get project:
```
git clone https://github.com/ox223252/Configure.git
```

make it executable:
```
chmod +x Configure/configure
```

create makefile and config's folder:
```
./Configure/configure
```

call dialog box to configure makefile:
```
./Configure/configure
```

compile projet:
```
make
```

remove all \*.o and \*.so filles
```
make clean
```

remove all *\*.o*, *\*.so*, *exec* and files in *bin/out* and *doc* directory
```
make mrproper
```

remove all files generated automaticly, keep folders (I use it before create tar):
- .
- ..
- .config/\*
- .git/\*
- Configure/\*
- lib/\*
- patch/\*
- res/\*
- src/\*
and files:
- configure
```
make empty
```

the makefile config can be overwrite manually to change the output with this values:
```
<var label>=<default value> (<available values>)
GDB=off (on)
GPROF=off (on)
FULL_CPP=off (on)
pthread=off (on)
sdl.1=off (on)
sdl.2=off (on)
realTime=off (on)
math=off (on)
ssl=off (on)
cares=off (on)
crypto=off (on)
use_DLL=off (on)
create_DLL=off (on)
LINKAGE=dynamique (static)
OPTIMISATION=-O0 (-O1/-O2/-O3)
OUT_DLL=static (dynamic)
WARNING=std (non/all)
EXEC=exec (<name of exec>)
OUTFOLDER=out (<name of folder used for exec outputs>)
ROOT_DIR=bin (<name of root folder for exec binary>)
DOC_DIR=doc (<name of documentation>)
SOURCE_DIR=src (<name of sources>)
RESSOURCES_DIR=res (<name of ressources[if needed]>)
LIB_DIR=lib (<name of additionals libs>)
CONFIG_DIR=.config (<name of config folder>)
CC=gcc (<C compiler [natif]>)
CXX=g++ (<C++ compiler [natif]>)
LABEL=arm (<label for cross tool>)
HARD_ARCH=natif (<LABEL[use for next compilation]>)
CROSS_CC=arm-linux-gnueabi-gcc (<C compiler [corss]>)
CROSS_CXX=arm-linux-gnueabi-g++ (<C++ compiler [corss]>)
LIB= (<path of additionals libs>)
```

for example this command will generate a cross compiled binary for arm with gdb activated.
```
make HARD_ARCH=arm GDB=on
```