# Configure

## Purpose

This script will permit to generate and configure makefile easily, with dialog box or config file, for C or C++ projects.

## Usage
### Init:
Create makefile and config's folder:
```shell
./Configure/configure
```
This will display nothing, only create files and folders.

Call dialog box to configure makefile:
```shell
./Configure/configure
```
This cmd will display somes GUI:

![ihm](ihm_1.png)

```SHell
.
├── Tool chaine
│   ├── lib
│   │   ├── [ ] pthread
│   │   ├── [ ] sdl.1
│   │   ├── [ ] sdl.2
│   │   ├── [ ] realtime
│   │   ├── [ ] math
│   │   ├── [ ] ssl
│   │   ├── [ ] cares
│   │   ├── [ ] crypto
│   │   ├── [ ] use_DLL
│   │   └── [ ] create_DLL
│   └── Tools**
│       ├── FLAGS=
│       ├── CC=
│       ├── CXX=
│       ├── natif_FLAGS=
│       ├── natif_LIBS=
│       ├── LABEL=arm
│       ├── arm_CROSS_CC=
│       ├── arm_CROSS_CXX=
│       ├── arm_FLAGS=
│       ├── arm_LIBS=
│       ├── arm_EXEC_AFTER=
│       ├── LABEL=w64
│       ├── w64_CROSS_CC=
│       ├── w64_CROSS_CXX=
│       ├── w64_FLAGS=
│       ├── w64_LIBS=
│       └── w64_EXEC_AFTER=
├── Options
│   ├── Hardware arch : xxx
│   │   ├── [ ] native compilation
│   │   └── [ ] cross compilation for <name>
│   ├── Warnning : xxx
│   │   ├── [ ] standard
│   │   ├── [ ] no warning
│   │   └── [ ] all warnings
│   ├── Optimisation : xxx
│   │   ├── [ ] none
│   │   ├── [ ] minimal
│   │   ├── [ ] binary_size
│   │   └── [ ] execution_speed
│   ├── Linkage : xxx
│   │   ├── [ ] dynamic
│   │   └── [ ] static
│   ├── Debug
│   │   ├── [ ] GDB
│   │   ├── [ ] GPROF
│   │   └── [ ] FULL_CPP
│   └── Out : xxx
│       ├── [ ] binary
│       └── [ ] shared_lib
├── Path
│   ├── EXEC=
│   ├── OUTFOLDER=
│   ├── ROOT_DIR=
│   ├── DOC_DIR=
│   ├── SOURCE_DIR=
│   ├── PATCH_DIR=
│   ├── RESSOURCES_DIR=
│   ├── CONFIG_DIR=
│   └── LIB_DIR=
├── Mode
│   ├── [ ] compiled_with_debug_logs
│   └── [ ] compiled_without_debug_log
├── Patch
│   └── [ ] not working
├── Git
│   └── *see note
└── Compiler
```
##### \*Note:
The git option will request a github name and a clone root directory. Once it's done, the script will use curl to request to github the repo's name.

#### \*\*Note:
The Tools file could be feed with new toolchains without limitation, you just need to follow the template exemple. The LABEL definition should be defined for each compilation tool set.
```
LABEL=<name>
<name>_CC=toolchain for C compilation
<name>_CXX=toolchain for C++ compilation
<name>_FLAGS=flags for this toolchain
<name>_LIBS=libs for this toolchain
<name>_EXEC_AFTER=cmd executed once compilation was done (could execute a script)
```

If git init was done, then new repos cloned will be add as git's submodules.

### Compile projet:
```shell
make
```

### Remove all temporary files:
Remove \*.o and \*.so filles
```shell
make clean
```

### Clean harder:
Remove all *\*.o*, *\*.so*, *exec* and files in *bin/out* and *doc* directory
```shell
make mrproper
```

### Clean full project:
Remove all files generated automaticly (I use it before create tar).

keep folders:
  - .
  - ..
  - .config/\*
  - .git/\*
  - Configure/\*
  - lib/\*
  - patch/\*
  - res/\*
  - src/\*

keep files:
- configure
```shell
make empty
```

### Advanced
the makefile config can be overwrite manually to change the output with this values:

| var label 		| default value | available values 						|
| ---				| ---			| ---									|
| GDB 				| off 			| on 									|
| GPROF 			| off 			| on 									|
| FULL_CPP 			| off 			| on 									|
| pthread 			| off 			| on 									|
| sdl.1 			| off 			| on 									|
| sdl.2				| off 			| on 									|
| realTime 			| off 			| on 									|
| path 				| off 			| on 									|
| ssl 				| off 			| on 									|
| cares 			| off 			| on 									|
| crypto 			| off 			| on 									|
| use_DLL 			| off 			| on 									|
| create_DLL 		| off 			| on 									|
| LINKAGE			| dynamique 	| static								|
| OPTIMISATION 		| -O0 			| -O1/-O2/-O3 							|
| OUT_DLL 			| static 		| dynamic								|
| WARNING 			| std 			| non/all								|
| EXEC 				| exec			| name of exec							|
| OUTFOLDER 		| out			| name of folder used for exec outputs 	|
| ROOT_DIR 			| bin			| name of root folder for exec binary 	|
| DOC_DIR 			| doc			| name of documentation 				|
| SOURCE_DIR 		| src 			| name of sources						|
| RESSOURCES_DIR 	| res 			| name of ressources[if needed] 		|
| LIB_DIR 			| lib 			| name of additionals libs 				|
| CONFIG_DIR 		| .config 		| name of config folder 				|
| LIB 				|				| path of additionals libs 				|
| HARD_ARCH 		| natif			| LABEL[use for next compilation] 		|
| CC 				| gcc			| C compiler [natif] 					|
| CXX 				| g++			| C++ compiler [natif] 					|
| natif_FLAGS**		|				|										|
| natif_LIBS**		|				|										|
| LABEL** 			| arm/w64		| label for cross tool 					|
| arm_CROSS_CC**	| arm-linux-gnueabi-gcc | C compiler arm Linux			|
| arm_CROSS_CXX**	| arm-linux-gnueabi-g++ | C++ compiler arm Linux		|
| arm_FLAGS**		|				|										|
| arm_LIBS**		|				|										|
| arm_EXEC_AFTER**	|				|										|
| w64_CROSS_CC** 	| i686-w64-mingw-gcc | C compiler windows 64 bits 		|
| w64_CROSS_CXX**	| i686-w64-mingw-g++ | C++ compiler windows 64 bits 	|
| w64_FLAGS**		|				|										|
| w64_LIBS**		|				|										|
| w64_EXEC_AFTER**	|				|										|


for example this command will generate a cross compiled binary for arm with gdb activated.
```shell
make HARD_ARCH=arm GDB=on
```


### Tree examples:
After *git clone*:
```shell
.
├── Configure
│   ├── configure
│   ├── LICENSE
│   └── readme.md
├── res
│   └── LICENSE
└── src
    ├── lib
    │   ├── function.c
    │   └── function.h
    └── main.c
```

After *make*:
```shell
.
├── bin
│   ├── out
│   └── exec
├── Configure
│   ├── configure
│   ├── LICENSE
│   └── readme.md
├── makefile
├── makefile.bak
├── res
│   └── LICENSE
└── src
    ├── lib
    │   ├── function.c
    │   ├── function.h
    │   └── function.o
    ├── main.c
    └── main.o
```

After *make empty*:
```shell
.
├── Configure
│   ├── configure
│   ├── LICENSE
│   └── readme.md
├── res
│   └── LICENSE
└── src
    ├── lib
    │   ├── function.c
    │   └── function.h
    └── main.c
```

## Auto defines:
### Date of compilation:
To add the date of compilation to your binary file in your sources code add :

```C
...
printf ( "date %s\n", DATE_BUILD );
...
```

## [Auto main](initMain.md):
You can use this script to creante and feed a basic main, according with the included libs configs.

The minimal main is defined as it:

```C
// file auto generated

// INIT_FUNCTION

int main ( int argc, char ** argv )
{
	// INIT_VAR

	// INIT_CORE

	// END_CORE

	return ( 0 );
}

```