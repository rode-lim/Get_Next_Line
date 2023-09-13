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
That function is going to read lines, therefore it's name `read_line`.
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


NOW WE MOVE TO THE FIRST CREATED FUNCTION `read_line`!

First we define the function:
```
char    *read_line(int fd, char *buffer, char *hold)
```
Obviously the () have the contents we sent before on the previous function.

Now we declere two local variables and assign the value to one of them:char    *protects(char *get_line)
{
        size_t  i;
        char    *hold;

        i = 0;
        while (get_line[i] != '\0' && get_line[i] != '\n')
                i++;
        if (get_line[i] == '\0')
                return (NULL);
        hold = ft_substr(get_line, i + 1, ft_strlen(get_line) - i);
        if (*hold == '\0')
        {
                free(hold);
                hold = NULL;
        }
        get_line[i + 1] = '\0';
        return (hold);
}

```
{
    int    readline;
    char    *temp;

    readline = 1;
```
We start our loop that will continue as long as readline is not '\0'.
```
    while (readline != '\0')
    {
```
Now we use read function to read data from the file descriptor and store it in the buffer.
The number of characters read is stored in `readline` and will read a maximum of `BUFFER_SIZE` bytes.
```
        readline = read(fd, buffer, BUFFER_SIZE);
```
Using an `if` statement we are going to check if `readline` is equal to -1, which would indicate if an error occurred, if that's the case the function returns 0.
```
        if (readline == -1)
            return (0);
```
Now the loop checks if `readline` is equal to 0, in which case means that we reached the end of the file, so we must break the `while` loop using `break`.
```
        else if (readline == 0)
            break ;
```
The next line sets the character at the position `readline` in the `buffer` array to the character '\0', to therefore terminate the string.
```
        buffer[readline] = '\0';
```
To proceed make a `if` statement that checks if the `hold` pointer is null. If it is, it will allocate memory for a new string and initalizes it to an empty string using `ft_strdup`.
```
        if (hold == NULL)
            hold = ft_strdup("");
```
Assign `temp` the value of `hold` to allow us to keep track of the original `hold` string.
```
        temp = hold;
```
Concatenate the `temp` and `buffer` strings and assign the result to the `hold` pointer using `ft_strjoin`.
This will effectively append the newly read data to the existing `hold` string.
```
        hold = ft_strjoin(temp, buffer);
```
Free `temp` to prevent memory leaks and set it to `NULL` to ensure it doesnt point to any memory location after it has been freed.
```
        free(temp);
        temp = NULL;
```
Make an `if` statemente to check if theres  newline character ('\n') in the `buffer`. If there is one it breaks out of the while loop assuming that the line of imput has been read.
```
        if (ft_strchr(buffer, '\n'))
            break ;
        }
```
Finally return `hold` and it should contain the concatenated lines read from the file.
```
    return (hold);
}
```

Wow...We actually finished another function.
Good job. One more to go!


Now we learn to do `protects`:

First we obviously make the function defenition:
```
char    *protects(char *get_line)
{
```
we are going to add 2 variables a `size_t` and a `char *`
Hold is going to have the result and i is going to serve as a counter.
```
    size_t    i;
    char    *hold;

    i = 0;
```
(We place i = to 0 as its going to inicialize the value on the position 0.)

we are now going to make a while that's going to increment `i` until it reaches a null character or a new line:
```
    while (get_line[i] != '\0' && get_line[i] != '\n')
        i++;
```
now we check if the loop ended because we reached the end of the string by doing a `if`:
```
    if (get_line[i] == '\0')
        return (NULL);
```
The next line calls a function named `ft_substr` to extract a substring from the `get_line` string. It starts at the character following the newline character (or the end of the string if no newline was found) and goes up to the end of the string. The result is assigned to the `hold` variable.
```
    hold = ft_substr(get_line, i + 1, ft_strlen(get_line) - i);
```
(in case you dont know `strlen` is a function that see's the length of a string.)

Now we check if the first character of `hold` is a null terminator and if it is we know the extracted substr is empty. In this case we free the memory occupied by `hold` using `free` and set `hold` to `NULL` to acoid potential memory leaks.
```
    if (*hold == '\0')
    {
        free(hold);
        hold = NULL;
    }
```
Now we truncate the original string removing everything after the newline chracter (or at the end of the string):
```
    get_line[i + 1] = '\0';
```
Finally. the function returns the `hold` pointer as said in the beggining. This will either point to a non empty substrin, the original `get_line` string OR `NULL` if the original string was empty or had no newline characters.

The purpose of this function is to protect the first part of the input string up the the first newline chracter and return the remaining part of the string.

#### 🐲 Checkpoint 3/3: get_next_utils.c

Wow you made it. Since utils are basic functions that only 42 requires I will leave here the final code instead of making a whole tutorial:

```
#include "get_next_line.h"
```
Include your header file.

```
char	*ft_strjoin(char const *s1, char const *s2)
{
	int		i;
	int		j;
	char	*str;

	i = 0;
	j = 0;
	str = (char *)malloc(sizeof(char) * (ft_strlen(s1) + ft_strlen(s2) + 1));
	if (str == NULL)
	{
		return (NULL);
	}
	while (s1[i] != '\0')
	{
		str[i] = s1[i];
		i++;
	}
	while (s2[j] != '\0')
	{
		str[i] = s2[j];
		i++;
		j++;
	}
	str[i] = '\0';
	return (str);
}
```
This function joins 2 strings together.
```
char	*ft_strdup(const char *s)
{
	int		i;
	int		j;
	char	*str;

	i = 0;
	j = 0;
	while (s[j] != '\0')
	{
		j++;
	}
	str = (char *)malloc(sizeof(*str) * (j + 1));
	if (str == NULL)
		return (NULL);
	while (i < j)
	{
		str[i] = s[i];
		i++;
	}
	str[i] = '\0';
	return (str);
}
```
This function dupes a string.
```
char	*ft_strchr(const char *s, int i)
{
	while (*s != '\0' && (unsigned char)i != *s)
		s++;
	if ((unsigned char)i == *s)
		return ((char *)s);
	return (0);
}
```
this code is a function that searches for a specific character in a null-terminated string and returns a pointer to the first occurrence of that character in the string if found. If the character is not found, it returns `0`.
```
size_t	ft_strlen(char const *str)
{
	int	i;

	i = 0;
	while (str[i] != '\0')
	{
		i++;
	}
	return (i);
}
```
This checks for the lenght of a null terminated string.
```
char	*ft_substr(char const *s, unsigned int start, size_t len)
{
	size_t	j;
	char	*str;

	if (start >= ft_strlen(s))
	{
		str = (char *)malloc(sizeof(char));
		*str = 0;
		return (str);
	}
	if (len >= ft_strlen(s))
		len = ft_strlen(s) - start;
	str = (char *)malloc(sizeof(char) * (len + 1));
	if (str == NULL)
		return (NULL);
	j = 0;
	while (start < ft_strlen(s) && j < len)
	{
		str[j++] = s[start++];
	}
	str[j] = '\0';
	return (str);
}
```
this checks for a substring inside a string.

## End...

Congrats you have finished `get_next_line`, double check the file names and you should be ready to deliver.

Don't forget headers!
Check the files above for the order of functions and a complete vew of the code:
[get_next_line.h](https://github.com/rode-lim/Get_Next_Line/blob/main/get_next_line.h)
[get_next_line.c](https://github.com/rode-lim/Get_Next_Line/blob/main/get_next_line.c)
[get_next_line_utils.c](https://github.com/rode-lim/Get_Next_Line/blob/main/get_next_line_utils.c)
