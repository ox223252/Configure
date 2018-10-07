## 

## Dev part:
to create a new lib that include this functionnality, you should follow somes rules:

```Shell
<lib name>
├── init
│   ├── <lib name>.head
│   └── <lib name>.init
├── source.c
└── source.h
```

### \*.head:
in the \*.head file you should put the includes
```C
#include "$SRC/source.h"
```
Don't forget to add an empty line to the end of file

Here you can use the var `$SRC` to replace the real path

### \*.init
in the \*.init file you should put the source code
```C
@ after <LABEL_ID>
	// INIT_LIB_LABEL_ID
	printf ( "your code here\n" );
	// END_LIB_LABEL_ID

@ before <LABEL_ID>
	printf ( "your code here\n" );

```

Don't forget to add an empty line to the end of file

