`list.append()`: Adds an element at the end of the list

`clear()`: Removes all elements from the list

`count()`: Returns the number of elements with the specified value

`index()`: Returns the index of the specified value

`remove()`: Removes the first item with the specified value

`pop()`: Removes the element with the specified position form the list

`insert()`: Inserts an element at the specified position

`reverse()`: Reverses the list

`len()`: Get the length of the list

`sort()`: Sort the list alphabetically

`range()` allows users to generate a series of numbers within a start and end point. Depending on how many arguments the user is passing to the function, they can decide where that series of numbers will begin, end, and how big the difference will be between one number and the next.\
`range(start, stop, skip)`

`isalnum():` Returns True if all characters in the string are alphanumeric

`isalpha():` Returns True if all characters in the string are in the alphabet

`isascii():` Returns True if all characters in the string are ascii characters

`isdecimal():` Returns True if all characters in the string are decimals

`isnumeric():` Returns True if all characters are numeric

`isdigit():` Returns True if all characters in the string are digits

`islower():` Returns True if all characters in the string are lower case

`isupper():` Returns True if all characters in the string are upper case

-   `close()` Closes the file
-   `read()` Returns the file content
-   `readline()` Returns one line from the file
-   `readlines()` Returns a list of lines from the file
-   `seek()` Change the file position
-   `tell()` Returns the current file position

Let's start with the `open` method. The command is: `file_name=open('file_name',mode)`

Here are descriptions of all the modes:

-   `r`: Opens a file for reading.
-   `w`: Opens a file for writing. Creates a new file if it does not exist or truncates the file if it exists.
-   `x`: Opens a file for exclusive creation. If the file already exists, the operation fails.
-   `a`: Opens a file for appending at the end of the file without truncating it. Creates a new file if it does not exist.
-   `t`: Opens in text mode.
-   `b`: Opens in binary mode.
-   `+`: Opens a file for updating.

-   `clear()`: Removes all items from the dictionary.
-   `get(key[,d])`: Returns the value of the key. If the key does not exist, returns d (defaults to None).
-   `items()`: Returns a new object of the dictionary's items in (key, value) format.
-   `keys()`: Returns a new object of the dictionary's keys.
-   `pop(key[,d])`: Removes the item with the key and returns its value or d if key is not found. If d is not provided and the key is not found, it raises KeyError.
-   `popitem()`: Removes and returns an arbitrary item (key, value). Raises KeyError if the dictionary is empty.
-   `update([other])`: Updates the dictionary with the key/value pairs from other, overwriting existing keys.
-   `values()`: Returns a new object of the dictionary's values.