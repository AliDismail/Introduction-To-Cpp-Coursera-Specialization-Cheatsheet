


# **2nd Course: Vectors, Pointers, Strings, and Files**

C++ is a high-level programming language. It was developed in 1983 by Bjarne Stroustrup at Bell Labs. It is used for developing various applications.

### 1. Arrays:

1. Basics:
An array is a data structure that stores a collection of data such as int, double, string, etc. This data is referred to as elements and each element has an index starting from 0 to length of the array.
```
int ages[5] = {1,2,3,4,5};
cout<<ages<<endl;
cout<< ages[2]<<endl;
ages[2]=7;
```
In this example we initialized a 5 elements integer array whish starts from 0 to 4 and doesn’t accept any other input then integer.

The first `cout` command prints out the array, the second one prints the third element in the array.

The final command changes the third element from 3 to 7.

2. 1D Arrays:

	The 1D array is an array that has one line of data

	To initialize the array, we specify the data type that the array will store then Declare the variable name for the array followed by the number of elements you want the array to hold within brackets.
```
string names[3]={“Bob”, “Fred”, “Alex” };
```
3. 2D Arrays:

	The 2D array is an array that takes the shape of a nxm table made of n rows and m columns.

	To initialize the array, we specify the data type that the array will store then Declare the variable name for the array followed by the number of rows you want the array to hold within the first brackets and the number of columns you want the array to hold within the second brackets.
```
double grades[2][3]={ };
```
4. Size:

	In C++, the `sizeof()` command returns the size of the array in bytes. So, to calculate the size of an 1D array we need to divide the size of the array in bytes with the size of an element in bytes.
```
int age[5] ={1,2,3,4,5};

int arraySize = sizeof(age) / sizeof(age[0]);
```
And to calculate the number of rows and columns in a 2D array you need to divide the size of the array in bytes with the size of a row for the rows and with the data type of the array for the columns and by the size of one element for the total size.
```
int age[3][3] = { {1, 2, 3}, {4, 5, 6}, {7, 8, 9} };
totalElements = sizeof(age) / sizeof(age[0][0]);
int numRows = sizeof(age) / sizeof(age[0]);
int numCols = sizeof(age[0]) / sizeof(int);
```
5. Iteration:

	We can use loops that we discussed before to add element to the array and print it out
```
int age[5];
for(int i =0; i<5;i++){
	age[i]=i+1;
	cout<<age[i]<<endl;
}
int arraySize = sizeof(age) / sizeof(age[0]);
for(int j=0; j<arraySize;j++){
	age[j]=5;
	cout<<age[j]<<endl;
}
```
### 2. Vectors:

1. Basics:

	Vectors are a data structure that function as the flexible version of the array as unlike arrays you can make changes to its size within the code.

	To use vectors, you need to include #include <vector> in the header of your program.

	To create a vector, you need to include the following:

	* The keyword vector followed by the data type in angle brackets <>.

	* A variable name that refers to the vector.

	* The number of elements the vector can hold within parentheses ().
```
vector<int> numbers(3); //initialize a 3 slots vector
cout<<numbers<<endl; // prints the content of the vector
vector<int> ages{1,2,3,4};
cout<<ages<<endl;
```
2. Functions:

	To refer to or change an element at an index we use the `at(idx)` method.
```
vector<int> numbers(3);
cout<<numbers.at(0)<<endl; // print the element of the vector at index 0
numbers.at(0) = 23; // changes the element at 0 to 23
cout<<numbers.at(0)<<endl;
```

To insert an element at the end of the vector we use the `push_back(element)` method.
```
vector<int> numbers(3);
numbers.push_back(50); // adds a forth slot the vector and stores 50 in it
cout<<numbers.at(2);
```
To remove an element at the end of the vector we use the `pop_back()` method.
```
vector<int> numbers(3);
numbers.push_back(50);
cout<<numbers.at(3);
number.pop_back(); // removes the 50 since its the last element
cout<<numbers.at(3);
```
To insert an element at a specific index we use the `insert(idx,element)` method and the `begin()` method to indicate the index.
```
vector<int> numbers {1,2,3};
numbers.insert(numbers.begin()+1,30); // adds a 30 between the first and second slots making the original second slot the third and respectively pushing the other to the right
cout<<numbers<<endl;
```
To remove an element at a specific index we use the `erase()` method and the `begin()` method to indicate the index.
```
vector<int> numbers {1,2,3};

numbers.push_back(0);
numbers.erase(mumbers.begin());// removes the first slot and making the second the first and respectively pushing the rest to the left
cout<<numbers.at(2)<<endl;
```
To calculate the size of the vector we use the `size()` method.
```
vector<int> numbers(3);
numbers.push_back(50);
cout<<numbers.size(); // returns the size which is equal to 4
```
3. Iterate:

	Similarly to the arrays we can iterate threw a vector to add element, remove, print, and change values and other uses that depends on the algorithm.
```
vector<int> numbers(3);
for(int idx = 0; idx<numbers.size();i++){
	numbers.at(idx) = idx+2; // this loop changes the elements of the vector to the chosen order
}
cout<< numbers<<endl;
```
### 3. Pointers:

A pointer is a data type that stores a memory address of another piece of data. Pointers point to the memory address of the data that they are associated with.

All pointers have a data type and a name that they are referred to. To declare a pointer, you need to have the following syntax in order:

* The data type of the pointer (e.g. int, string, etc.).

* An asterisk symbol *.

* A name for the pointer.
```
int* p ;
cout<< p<<endl; // it prints the memory location
```
To utilize the pointer, we need to reference and dereference to the pointer.

To reference to the pointer, we need to use the reference operator which is the and “&” before the referenced element when used.
```
int a = 22;
int* p= &a;
cout<<p;// prints the memory location
```
To dereference to the pointer, we need to use the reference operator which is the asterisk “*” before the pointer when used.
```
int a = 22;
int* p= &a;
cout<<*p;// prints 22
```
You can reference a pointer to another pointer, but you need to keep in mind that the dereference operator refer to latest reference which why you will find yourself using more then 1 dereference operator after each other and it refers to the level of pointers referred to each other.
```
int a = 5;
int* p = &a;
int** p2 = &p;
cout << *p << endl; // prints 5
cout << **p2 << endl; // prints 5
cout << *p2 << endl; // prints memory location of p
```
### 4. Strings
1. Basics

A string is a collection of characters surrounded by double quotes. The string data type is used to store words or sentences.

A string is a zero based index meaning it starts with zero as an index.

The string data type is part of the Standard Library and is defined in the <string> header file.

We must include `<string>` header file for using string class.
```
string str = “Hello world!!”;
cout<< str<<endl;
```
In strings to there is a thing called escape characters that will help us use reserved characters such as the quote and the double quote. Escape characters always start with a backslash `\`.

- `\n` jumps on the next line.

- `\t` creates a Tab space.

- `\\` prints a backslash.

- `\'` prints a quote.

- `\”` prints a double quote.

2. Functions

To get the length of the string we use the function `length()`.

To get the character at a specific index in a string we use the function `at(idx)`.

To find a specific string inside a string we use the function `find(“str”)`. If the string is not found it returns 8446744073709551615 which equivalent to -1 and the index if found. You can also specify the starting index of the search using `find(“str”, idx)` version of the function.

To get a specified substring in the string we use the function `substr(start_idx, nbr_of_char)`. Note that if the number of the characters is not specified the substring function will copy everything from the starting index to the end of the original string.

To find the first appearance of string inside a string we use the `find_first_of(“str”)` function. If the string is not found it returns 8446744073709551615 which equivalent to -1 and the index if found. You can also specify the starting index of the search using `find_first_of(“str”, idx)` version of the function.

To find the last appearance of string inside a string we use the `find_last_of(“str”)` function. If the string is not found it returns 8446744073709551615 which equivalent to -1 and the index if found. You can also specify the starting index of the search using `find_last_of(“str”, idx)` version of the function.

To insert a character at the end of the string we use the `push_back(‘a’)` function.

Top insert a string in a string at any index we use the `insert(idx,“str”)` function.

To remove a character from the end of the string we use the `pop_back()` function.

To remove a number of characters starting an index to certain number of characters from inside the main string we use the `erase(idx,nbr_of_char)` function. If the number of characters is not specified the function deletes everything from the starting index to the end of the main string. If the parentheses are left empty the whole string will be deleted.

The `replace(start_idx,nbr_of_char,“str”)` function combines the functionality of the erase and insert functions in a one function.

To concatenate two strings other then using the plus operator is threw the `append(“str”)` function.

To get the uppercase version of char we use the `toupper(‘a’)` function.

To get the lowercase version of char we use the `tolower(‘A’)` function.
```
string str1 = "Potatos";
string str2 = "are delicious";

int length_of_str = str1.length();// gets the length of str1
int idx_of_Po = str1.find("Po");// search for Po inside the str1
cout<<str1.append(str2)<<endl;
```
3. Iteration

We can use a loop to iterate over a string which allows us to deal with every single character in the string.

4. Comparison

To compare between strings, we can use `==` to check if they are equal and `!=` to check if they are different. Also, we can use the `str1.compare(str2)` function, this function uses the lexicographical order to determine the results. If it returns a negative number it means str1 comes first, if positive it means str2 comes first, and if 0 the strings are equal

Lexicographically speaking, empty strings always come first, followed by numbers, then uppercase letters, and finally lowercase letters.



