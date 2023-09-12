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

(Disclaimer: I'd like to note that we must understand this project is done through my view and I hope you understand in this tutorial its gonna be displayed with my POV, if you need any help just ask me.
so lets get started?)

So whats the first step?
Let's make the main function.

(For 42 students: Don't forget to add the header to your file)
We must start by adding the header we just created so...

```
#include "get_next_line.h"
```
Now we add the function declaration to start our work:

```
char    *get_next_line(int fd)
{
    
}
```
Now let's start by defining our variables.
```
char            *get_line;
static char     *hold;
char            *buffer;
```
What do they do?


get_line:
This will be used to store the line read from the file.


hold:
The use of static means that the variable retains its value between function calls, acting as a kind of "memory" for the function.


buffer:
This pointer will be used to allocate a temporary buffer for reading data from the file.


Now we move on...
we are going to create the first if in our function.

This if is going to see if the fd(file descriptor) or the buffer is lower or the same(<=) as 0.
```
if (fd < 0 || BUFFER_SIZE <= 0)
      return (0);
```
If this turns out to be true it's going to return 0.


Now we are going to allocate memory for the 'buffer' using the 'malloc' function. we will need it to allocate 'buffer size + 1' to store the read data, plus a null terminator.
The result will be cast to a 'char *' and assigned to 'buffer'.
```
buffer = (char *)malloc(sizeof(char) * (BUFFER_SIZE + 1));
```
We mus now add the second "*if*" of this function. This if is goig to check if the allocation of memory for 'buffer' was successful. If it wasnt and 'buffer' is '\0' (NULL) it's going to return 0.
```
if (buffer == '\0')
    return (0);
```
