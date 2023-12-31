# Makefile

- Decide wich part need to be recompile
- Series of instruction to run
- Depend on what file change
- Written for **Gnu Make**

```bash
hello:
    echo "Hello, World!'
```

- Output will be like this

```bash
$ make
echo "Hello, World"
Hello, World
```

```bash
blah: blah.o
	cc blah.o -o blah

blah.o: blah.c
	cc -c blah.c -o blah.o 

blah.c:
	echo "int main() {return 0; }" > blah.c
```
- Makefile will run top to bottom
- After `:` is dependencies
- If have dependencies, go next line
- If no dependencies, run

```bash
blah.c:
	echo 'hello'
```

- If file `blah.c` don't exist run this command
- If run once again, not detect if update or not
- Because file blah not exist

```bash
targets: prerequisites
    command
    command
    command
```
- `targets` are filename
- Separated by _space_
- Typically only on per rule
- `command` are series of step
- To make the target
- To write command, start with **tab**
- Don' use space for indentation
- `prerequisites` also **file name**
- Separates by _spaces_
- It must be **exist** before 
- The target run
- Also called **dependencies**

```bash
hello:
	echo 'hello world'
	echo 'this will run if file not exist'
```

- Output `make hello`

```bash
echo 'hello world'
hello world
echo 'this will run if file not exist'
this will run if file not exist
```

- As long hello is _not exist_
- Command will run, if _exist_ not run
- _Targets_ and _file_ are same thing
- If no _prerequisites_, make not check _file_ 

```bash
blah: blah.c
	gcc -c blah.c -o blah
```

- The logic is `if not exist` or `blah.c` is newer timestamp
- Run the command, (don't manuallly change change timestamp)
- Command will run only after dependencies are finished

## Clean

- `clean` often use to remove output of targets
- It's not special keyword in `Makefile`
- If we want clean, we must explicitly call `make clean`
- It's not intended as filename, if has filename `clean`
- The target won't run
```bash
some_file: 
	touch some_file

clean:
	rm -f some_file
```

## Variable

- Can only be string
- Can use `:=`, but `=` also work

```bash
files := file1 file2

some_file: $(files)
	echo 'Look variable:' $(files)
	touch some_file

file1: 
	touch file1

file2:
	touch file2

clean:
	rm -f file1 file2 some_file
```

- Single or double quotes have no meaning to make
- There are character assign to variable
- Quote are useful to bash/shell or C function 
- Wheater it has quote when declare varible
- Or has quote in command

```bash
a := one two\n
b := 'one two\n'

all:
	printf '$a'
	printf $b
```

## Targets

- Making multiple target and run them all 
- Make `all` target
- Since it first rule, it will run by default
- It's will run one by one list in all 

```bash
all: one two three
one:
	touch one
two:
	touch two
three:
	touch three
clean:
	rm -f one two three
```

### Multiple target

- When it has multiple target, but only do one thing
- To run one by one targets use `$@` for each target
- `@` is automatic variable

```bash
all: f1.o f2.o
f1.o f2.o:
	echo $@
```

### Wildcard

- `*` and `%` are called wildtarget
- But meaning is different
- `*` search in filesystem for matching filename
- And wrap it in `wildcard` function
- It maybe use in in target, prerequisites or in wildcard function
- But don't use it in variable difinition
- It will return error if file no exist
- `wildcard` function if not exist is leave at is it

```bash
# wrong: *.o
right: $(wildcard *.o)
all: one two three four
# one: $(wrong)
two: *.o 
three: $(right)
four: $(wildcard *.o)
```

- `?` is list of prerequisites

```bash
print: $(wildcard *.c)
	ls -l $?
```

### % Wildcard

- Very useful, but confusing
- Because of variety of situation can be used
- When use in matching mode, it matches one or more
- Character in string, this match called stem 
- When use in replacing mode, it take stem was
- Matches and replaces in a string
- `%` is most often use in specific function

## Automatic variable
