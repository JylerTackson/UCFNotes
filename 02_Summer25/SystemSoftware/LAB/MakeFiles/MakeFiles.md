What is a make files?
- A script to automate the compilation of your build process.

Key concepts of Make files:
- Targets
- Dependencies
- Actions

Simple make files:
```
sum:main.o sum.o
	gcc -o sum main.o sum.o

main.o: main.c sum.h
	gcc -c main.c

sum.o:sum.c sum.h
	gcc -c sum.c
```
`sum:` Final Executable File
`main.o:` object file is created from `main.c` and includes `sum.h`
`sum.u:` created from `sum.c` and includes `sum.h`

If you have a file that is the same name as a target command within the make file you can use the command:
```
.PHONY:<targetName>
```
This will execute the target name rather than trying to target the object file you have created.

