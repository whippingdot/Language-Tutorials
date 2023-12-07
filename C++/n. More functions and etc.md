# More C++ Functions to Learn

This file contains a lot of information I myself I had learnt about C++ in a course. It might not cover all the topics and does not cover the essential basics (those are covered in previous files number 0-6). This can technically be considered the foundation for C++ as there is much more to learn that all of this.

Also, for almost all functions/classes (some old still contain the prefix) `std::` is removed due to its frequentness and how repeated it becomes as it is used on almost every function and class. If an error comes even though the right library is imported, try adding an `std::` before the function/class and check if that fixes the issue. Something else removed in some places and not removed in others is the semicolon(;), and it is removed in some places because that is how I wanted this file to be, but forgot midway through and started using semicolons again.

## `cstdlib` Library

### `strtol`

This function converts a part of a string to a long int. It requires the string or character array, a pointer, and finally a base power. The function is thus:

```
char *endptr = NULL;
base = 10;
long int integer = strtol(string.c_str(), &endptr, base);
```

In the example we took the base as 10. The point does have to point to NULL. I don't really understand how the function works but I will update it when I do

### `strtoll`

Same as `strtol` but converts a string to a long long int.

## `cstdio` Library

### Modes

These modes are for opening files.

The modes you can open in and more details about them are:
| Mode string | Meaning | If file exists | If file doesn't exist |
| ----------- | -------------------------- | ---------------- | --------------------- |
| r | Open file for reading | Read from start | Failure |
| w | Create a file for writing | Destroy contents | Create new file |
| a | Append to a file | Write from end | Create new file |
| r+ | Open file for read/write | Read from start | Failure |
| w+ | Create file for read/write | Destroy contents | Create new file |
| a+ | Open file for read/write | Read from start | Create new file |
| b | Binary mode | - | - |

### `FILE`

The `FILE` class is underneath the `cstdio` header. It is used to define `FILE` variables such as `stdout` and `stdin`.

### `stdout` and `stdin`

These are two variables of type `FILE`. When outputting to `stdout` you are basically printing something to the terminal, and when inputting from `stdin` you are basically getting values from the terminal.

### fopen

Used to open a file. The syntax is simple, consisting of just `FILE *varName = fopen(filePathStr_Var, {mode to open in, in double quotes})`.

### fclose

Used to close a file. The syntax is simple, consisting of just `fclose(varName)`. Make sure to close the file after opening it!

### fwrite

This is used to write to the file. fputs can alternately be used by just outputting to the file, but this is another way to do it. Its syntax is more complicated: `fwrite(bufferName_Var {if it is a struct, then you have to use the reference of ($) operator}, sizeof(buffer {actual struct name if struct}), numberOfSomething, FILE_Var)`.

### fread

This is used to read the file. Alternatively you can just loop through the file using fgets, but this is another way to do it. Its syntax is more complicated: `fread(bufferName_Var {if it is a struct, then you have to use the reference of ($) operator}, sizeof(buffer {actual struct name if struct}), numberOfSomething, FILE_Var)`.

### **NOTE:**

**Before using fwrite and fread, maybe do some research on them because lots of information is missing and I don't really know how to use them.**

### remove

I don't think this is specific to Input and Output, but you can use this to delete the file that you have created, or just any file in general. The syntax is simple: `remove(filePathStr_Var)`.

### rename

Again, don't think this is specific to Input and Output, but you can use this to rename a file to a different name. The syntax is simple: `rename(oldFilePathStr_Var, newFilePathStr_Var)`.

### printf

Used to print out formatted strings. The format is: `printf("Some string with %d formatted thing", 1)`. You can have an indefinite amount of arguments (I think) after the string. The string has to use specifiers to say what is getting formatted. A table with some format specifiers is below:

| Specifier | Meaning               |
| --------- | --------------------- |
| %d        | Integer number        |
| %f        | Floating point number |
| %s        | C-string              |
| %c        | Character             |
| %p        | Pointer               |
| %zd       | Sizeof                |
| %%        | The % character       |

### fprintf

Same as printf, but you have to specify where you are outputting your formatted string. This is useful when sending formatted strings to files. The syntax is `fprintf(FILE_Var, "Some string with %d formatted thing", 1)` \
You can output to variables of type 'FILE', which can be user-defined files, or already defined files like `stdout`.

### puts

This is used to output a string to the console; `puts("Some string here")`.

### fputs

Same as puts, but you can output things to a specific area; the syntax for this is `fputs(output_string, FILE_Var)`. \
You can output to variables of type 'FILE', which can be user-defined files, or already defined files like `stdout`.

### fgets

Used to get the file contents one line at a time. The syntax is pretty simple, being `fgets(buffer_charArray, bufferSize_int, FILE_Var)`. \
You can get an input using `stdin` as your FILE variable. You can also use this with a while loop to constantly get the contents of a file, until there is no more.

### fflush

Used to flush the contents of a FILE variable. The syntax is simple, being `fflush(FILE_Var)`. \
Flushing the contents of a FILE variable basically means that the other strings of tasks are stopped and have to wait for this to finish before they can continue. It allows the code to continue in the right order. `std::endl` automatically flushes the stream. You can also use `fflush(stdout)` to flush the output manually, like when using `puts`.

## `cstring` Library

For a lot of these functions you can remove the 'n' in the middle and get the same function - but without the maxLength.

### strncpy

This copies the string to a specific place. The format is more complex, being `strncpy(locationToCopy_Var, string, maxLength)`.

### strncat

This concatenates two strings. `strncat(locationToCopy_Var, concatingItem, maxLength)`.

### strnlen

This can be used to find the length of a C-String. The syntax is simple - `strnlen(c-string_name, maxLength)`.

### strcmp

Used to compare two strings, syntax is `strcmp(string1, string2)`. \
Returns 0 if they are the same, -1 if string1 is smaller, and 1 if string2 is smaller.

### strchr

Finding a character in a string. `strchr(string, character)`. \
Returns a pointer to the first occurrence of the character in the string, or if no occurrence is found returns NULL. To find the occurrence, subtract the string from the pointer variable containing the `strchr`.

### strstr

Finds a string in another string. `strstr(string, stringLookingFor)`. \
Returns a pointer to the first occurrence of the string in the string, or if no occurrence is found returns NULL. To find the occurrence, subtract the string from the pointer variable containing the `strstr`.

### strerror

This can be used to get the string message of an error using its error number. `strerror(errno)` is the format, where errno can be taken from the `cerrno` library.

This is in the C-String library as it is defined in a character pointer, and this can also be used in outputting.

## `cmath` Library

### abs

This function is also available in `cstdlib` I think. This is used to get the absolute value of a number. The syntax is simple - `abs(number)`.

Long and long long versions are also available, being `labs(number)` and `llabs(number)` respectively. \
In this library, to get the absolute value of a float and double, you have to use the function `fabs(number)`. For the long version it is `fabsl(number)`. But, in the `cstdlib` library you can just use `abs(number)` for both (I don't know about long, but for the normal double yes).

### exp

Again, this function is also available in `cstdlib`. This function is used to get the exponential of a number. The syntax is `exp(number)

### pow

I am starting to think all these functions are in both libraries (`cstdlib` as well). Use this and you get the power of a number. `pow(number, power)`.

### sqrt

Same as the above 3...You can use this to get the square root of a number. The syntax is `sqrt(number)`.

## `cerrno` Library

### errno

errno can be used to give the error number. You can use it while outputting strings or in other use cases.

### perror

perror is used to prepend a string before a colon and the error messages. The format is `perror("Cannot do this")`.

## STL (Standard Template Library)

All elements in the STL are in the STD namespace. Therefor they are preceded with `std::`. I will assume that you know this and no `std::` will be included.

### `vector` Library

Vectors are initialized with an initializer list. A vector's definition syntax is unique, being `vector<variableType> varName`, and initializing it is `vector<variableType> varName = {1, 2}`.

#### `.front()`

Used to get the first value.

#### `.back()`

Used to get the last value.

#### `.size()`

Used to get the size of the vector.

#### `.at()`

`.at(position)` is the syntax, and this is used to get the variable of a certain position. Alternatively using square brackets without `.at` also works.

#### Range-Based For Loop

You can also create a range based for loop when using vectors, for example:

```cpp
#include <iostream>
using namespace std;

vector<int> integerVector = vector<int>();

for (int i : integerVector) {
  cout << i << endl;
}
```

#### `.insert()`

This is used to insert a variable at a certain position. The position is defined by an iterator + an offset `vector.insert(vector.begin() + integerOffset, insertingValue)`.

#### `.erase()`

Used to erase a value from a vector, all that is needed is the position (iterator + offset) `vector.erase(vector.begin() + integerOffset)`.

#### `.push_back()`

This pushes a new value into the vector at the back. `vector.push_back(insertingValue)`.

#### Initializing from an Array

`vector<variableType> varName(array, array + sizeOfArray)` is a different initialization method to initialize from an array.

#### **Notes**

As vector is a template class (therefor it is in the Standard **Template** Library), it can be used with multiple different variable types. It can even contain other template classes such as strings.

### `string` Library

This class is a specially designed container used to operate with sequence of characters.

#### `stoi()`

This function can be used to convert a string to a regular int.

#### Concatenation using `+`

You can concatenate two strings using the plus symbol. `cout << string1 + string2 << endl`

#### `.size()` & `.length()`

These two are exactly the same, and output the length of the string.

#### Conditional Operators

You can use `==` and `>` and `<` operators with strings.

#### Range-Based For Loop

The same as vectors.

#### `.insert()` & `.erase()`

The same as vectors.

#### `.replace()`

This function is used to replace a few characters in a string. `string.replace(indexPositionStart, lengthNeededForChange, stringAdded)`.

#### `.substr()`

This function is used to get a substring from a string. `string.substr(indexPositionStart, lengthOfSubstring)`

#### `.find()`

find returns the first found position of the character that is given. `string.find(character)`.

#### `.rfind()`

rfind returns the last found position of the character that is given. `string.rfind(character)`.

### `iostream` Library

This library is mainly used for backend support, but there are few classes that you can generally use.

#### `cout`

cout stands for console output, which does exactly what it says - outputs to the console. This is an alternative to puts (though puts can't output variables) and printf.

Unlike printf, it uses bit moving operators (I think) to output stuff. The format is `cout << "text\n"`. In place of "text\n" you can have a variable such as an integer or a string variable, or just and integer in general. You con't need to specify any `%` to make it work.

#### `cin`

cin stands for console input, and takes the input of just the first word. This also uses bit moving operators (I think) and the format is `cin >> variable`.

cin automatically creates a new line after input.

#### `getline`

getline is a function for cin, in which it takes the whole line as input. The format is `cin.getline(string str, char/size_t MAX_LENGTH)`. Instead of string if you use a character array for 'str', using `sizeof()` will take the max length of the array and use that as a size_t value for the second parameter.

#### `right`

This right aligns text. `cout << right << "Woah!\n";`.

#### `left`

This left aligns text (default most of the time). `cout << left << "Woah!\n";`.

### `iomanip` Library

This library is used for things such as representing integers as hexadecimal, octal, those with showbase, etc.

#### `hex`

In a `cout` just add `hex` before the integers. Format - `cout << hex << 3 << endl;`.

#### `showbase`

In a `cout` just add `showbase` before the integers and hex/oct (for hex/octal) - `cout << showbase << hex << 3 << endl;`.

#### `oct`

In a `cout` just add `oct` for octal values before the integers. Format - `cout << oct << 3 << endl;`.

#### `noshowbase`

Cancels out the `showbase` if it was initialized in a `cout`. Format - `cout << showbase << noshowbase << 3 << endl;`.

#### `dec`

Prints in standard decimal form (again reverting the above) - `cout << showbase << hex << noshowbase << dec << 3 << endl;`.

#### `scientific`

For decimals (doubles), gives the exact value. Normally only till hundred thousandths is shown. `cout << scientific << 3.111232 << endl;`

#### `setprecision`

This sets the precision for how many decimal points is going to be outputted. `cout << setprecision(3) << 3.22342 << endl;`

#### `unsetf`

Unsure if this is only for reverting decimals but in the purpose I was given it is used to revert the decimal values to how they are normal represented - to the hundred thousandths place. `cout.unsetf(ios_base::floatfield)`.

#### `setw`

This sets the width of the string being formatted/outputted. `cout << setw(64) << "Woah!" << endl;`

#### `setfill`

setfill fills the empty space left in the line (such as when right aligning text everything on the left will be filled with the specified symbol). `cout << setfill('-') << right << "Woah!\n";`.

### `fstream` Library

This library is used for reading and writing in files. For more control, the C Standard Library is recommended.

#### `ofstream`

Opens a file for writing. `ofstream variableName(fileName);`.

Once you get the opened file, you can add text in it by using the same/a similar format to `cout`, such as using `<<` and the string/integer/variable you want to input all on the same line. `variableName << "Woah!\n";`.

#### `ifstream`

Opens a file for reading. `ifstream variableName(fileName);`.

#### `good`

This is used to check if you are at the end of the opened file (ifstream). `variableName.good()` results in a boolean value depending on whether you have reached the end or not.

#### `close`

Closes the opened file. `variableName.close();`.

### `exception` Library

#### `what`

The what function is added to the `std::exception` class in this library. `what` reports the error that was found. `cout << exceptionVariable.what() << endl;`.
