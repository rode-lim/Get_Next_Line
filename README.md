# Get_Next_Line 

This project involves programming a function that returns a line read from a file descriptor.

![Get_Next_Line](Get_next_line.png)

## Requirements

- Vim, Vscode, (your pick)...

## How to implement Get Next Line?

### Before we start (Disclaimer)

Hello, Dear Reader, I'm updating this project on GitHub, so if you find any mistakes, please report them to me. <3
Therefore, don't copy; learn. This project is designed for 42 School.

**Goals:**
According to the Subject, this project will teach us about static variables in C.

# 🐉 GET NEXT LINE GUIDE 🐉
## 1st step: Understanding 🐉

**Project name:** get_next_line

**Prototype:** `char *get_next_line(int fd);`

**Turn-in files:** `get_next_line.c`, `get_next_line_utils.c`, `get_next_line.h`

**External functions:** `read`, `malloc`, `free`

**PROHIBITED:**
- Using your libft
- `lseek()`
- Global Variables

**BONUS:**
EMPTY and I don't intend to do it.

## 2nd step: Files 🐲

The first thing I did in my projects was to create three files:

#### get_next_line.c
The main function where Get Next Line is going to be implemented.

#### get_next_line_utils.c
Secondary functions needed to run the main function.

#### get_next_line.h
Header file; this file is used to include all the necessary libraries, buffer size, etc...

## 3rd step: Coding... 🐲

As coding takes longer, I will go through the three files as checkpoints, starting with...

#### 🐲 Checkpoint 1/3: get_next_line.h
The first thing I did as a 42 student is to run ":Stdheader" command in Vim; this adds the 42 header to my project.

After that, the first part to do is to start the header file just like any other project:
```
#ifndef GET_NEXT_LINE_H
# define GET_NEXT_LINE_H
```

Now, add the libraries you think might be useful or search for someone who has all the required libraries:
```
# include <stdio.h>
# include <unistd.h>
# include <stdlib.h>
# include <fcntl.h>
```
Once you've picked your libraries, you are now ready to add the BUFFER_SIZE. Read the 42 header for a better explanation.
In summary, this code ensures that the macro BUFFER_SIZE is defined and set to 10 unless it was already defined elsewhere in the code:
```
# ifndef BUFFER_SIZE
#  define BUFFER_SIZE 10
# endif
```
I personally leave the file here and move on to the next file, but for the sake of the tutorial, I'm going to explain further.

You should now add the prototypes for your functions, for example:
```
size_t	ft_strlen(const char *str);
```
Repeat this until you have all your functions.

Now proceed to finish get_next_line.h by ending the definition:
```
#endif
```
#### 🐲 Checkpoint 2/3: get_next_line.c

(Disclaimer: I'd like to note that we must understand that this project is done from my perspective, and I hope you understand that in this tutorial, it's going to be presented from my point of view. If you need any help, just ask me.)

So, what's the first step? Let's create the main function.

(For 42 students: Don't forget to add the header to your file.)
We must start by adding the header we just created:

```
#include "get_next_line.h"
```
Now, add the function declaration to start our work:

```
char    *get_next_line(int fd)
{
    // Function implementation will go here
}
```
Now let's start by defining our variables:
```
char            *get_line;
static char     *hold;
char            *buffer;
```
What do they do?

`get_line:`
This will be used to store the line read from the file.

`hold:`
The use of static means that the variable retains its value between function calls, acting as a kind of "memory" for the function.

`buffer:`
This pointer will be used to allocate a temporary buffer for reading data from the file.

Now we move on. We are going to create the first `if` statement in our function. This `if` is going to check if the file descriptor `fd` or the buffer size is lower or the same (<=) as 0:
```
if (fd < 0 || BUFFER_SIZE <= 0)
      return (0);
```
If this turns out to be true, it's going to return 0.

Now we are going to allocate memory for the 'buffer' using the 'malloc' function. We will need it to allocate 'buffer size + 1' to store the read data, plus a null terminator. The result will be cast to a 'char *' and assigned to 'buffer':
```
buffer = (char *)malloc(sizeof(char) * (BUFFER_SIZE + 1));
```
We must now add the second `if` statement of this function. This `if` is going to check if the allocation of memory for 'buffer' was successful. If it wasn't and 'buffer' is '\0' (NULL), it's going to return 0:
```
if (buffer == '\0')
    return (0);
```
Now we give 'get_line' a new value.
The value we are going to give is the results of a function that we have yet to create.
That function is going to read lines, therefore it's name "read_line".
We must give the function, the `fd`, the `buffer` and `hold`.
```
get_line = read_line(fd, buffer, hold);
```
(As you see above, we gave `get_line` the value of `read_line`).

Now, to prevent any leaks, we must use the function 'free' on our 'buffer':
```
free(buffer);
```
Now we are going to set 'buffer' to 'NULL' to avoid using it after it has been freed:
```
buffer = NULL;
```
We will now add the last `if` statement that will check if 'get_line' is 'NULL':
```
if (get_line == NULL)
{
    free(hold)
    hold = NULL;
    return (NULL);
}
```
We use 'free' and '= NULL' for the same reasons as before.

However, we use 'return' to indicate that there are no lines available or an error occurred.

Now we are in the last stage of the main function, and we must create a function to protect. We will do that after the main function. Now, let's move on. Therefore, we are going to assign 'hold' the value of 'get_line' with the protection function, like the example:
```
hold = protects(get_line);
```
And we finalize by returning 'get_line':

```
    return (get_line);
}
```
This completes the explanation of the main function.
