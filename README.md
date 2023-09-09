# Get_Next_Line 
This project is about programming a function that returns a line read from a file descriptor.

![Get_Next_Line](Get_next_line.png)

==Requirements==
- Vim, Vscode, (your pick)...

## How to make get next line?

### Before we start (Disclaimer)

Hello Dear Reader, I'm making this project as I update the github, so if u find any mistake please report it to me. <3
Therefore don't copy, learn.
This project is made for 42 School.

Goals->
According to the Subject this project is going to teach us about static variables in C.

# 🐉GET NEXT LINE GUIDE🐉
## 1st step: Understanding🐉

Project name: get_next_line
Prototype: char *get_next_line(int fd);
Turn in files: get_next_line.c, get_next_line_utils.c, get_next_line.h
External functs: read, malloc, free

PROHIBITED:
- Using your libft
- lseek()
- Global Variables

BONUS:
EMPTY and I don't inteed to do it.

## 2nd step: Files🐲

The first thing I did in my projects was make 3 files:

#### get_next_line.c
Main function where get next line is going to be.

#### get_next_line_utils.c
Secondary funtions needed to run the main function.

#### get_next_line.h
Header file, this file is used to get all the libraries, buffersize, etc...

## 3rd step: Coding...🐲

As the coding takes longer I will go throught the 3 files as checkpoints, so first...

#### 🐲Checkpoint 1/3: get_next_line.h
The first thing I did as a 42 student is ":Stdheader" running this command on Vim will add the 42 header to my project.

After that the first part to do is start the header file so as any other project:
```
#ifndef GET_NEXT_LINE_H
# define GET_NEXT_LINE_H
```

Now add the libraries u think might be usefull or search for someone that has all the libraries required:
```
# include <stdio.h>
# include <unistd.h>
# include <stdlib.h>
# include <fcntl.h>
```
Once U pick ur libraries u are now ready to add the BUFFER_SIZE, read 42 header for a better explanation.
In summary, this code ensures that the macro BUFFER_SIZE is defined and set to 10 unless it was already defined elsewhere in the code.
```
# ifndef BUFFER_SIZE
#  define BUFFER_SIZE 10
# endif
```
I personally leave the file here and move on to the next file, but for the sake of the tutorial I'm going to explain already.

U should now add the prototip for your functions for e.g:
```
size_t	ft_strlen(const char *str);
```
Repeat this till u have all your functions.

Now proceed to finish get_next_line.h by ending the def.
```
#endif
```
#### 🐲Checkpoint 2/3: get_next_line.c

