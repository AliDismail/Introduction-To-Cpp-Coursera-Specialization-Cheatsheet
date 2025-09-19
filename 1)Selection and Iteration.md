


# **1st Course: Selection and Iteration**

C++ is a high-level programming language. It was developed in 1983 by Bjarne Stroustrup at Bell Labs. It is used for developing various applications.

### 1. Syntax:

For the first course we will only need to write code inside the main and we will be  ignoring other sections in the editor but don’t worry will be visiting them later.
```
Int main(){

//this where to write code

//this where to write code

}
```
An important note that to always end any line of code with the semicolon unless the code will not work.

### 2. Printing to console:

To print to console we use the command `cout` followed by `<<` then what we desire to print.
```
cout<< “Hello world!!”;
```
`cout` command stands for character out.

If you want to jump to a new line u follow the command with `endl` or use `\n` after what u want to print.
```
cout<<”Hello world!!”<<endl;

cout<<”Hello world!! \n”;
```


### 3. Comments:

Comments are lines of codes that are ignored, and they are written by the programmer to save information about a certain part in code.
```
Int main(){

//this code will print hello world to the console
cout<<”Hello world!!”<<endl;

}
```
For single line comments use double slashes `//`

For multi-line comments wrap the set of lines in `/* code is here */`.

### 3. Variables:

In computer science, we often need to use data. Variables are used to store a value for a particular type of data.

Each variable in C++ has:

1. A data type
	integer-float-double-boolean-string
2. A name:
	can contain alphabets, digits, and an underscore but the name of a variable must start 		with an alphabet or an underscore.
	
3. A value:

   Can be assigned directly to the variable or assigned/change later in the code.

To initiate a variable you need:
```
					(data type) (name) = (value);
```

### 4.Data Types:
1. Integer:

It is used to store integers.
Integers take 4 bytes of memory.
```
int var = 123;
```
2. Float:
It is used for storing single-precision floating-point numbers.
It takes 4 bytes of memory.
```
float var = 1.23;
```
3. Double:

	It is used to store double-precision floating point numbers.
	It takes 8 bytes of memory.
```
double var = 1.23;
```
4. Strings:

	A string is a collection of characters surrounded by double quotes. The string data type is used to store words or sentences.
```
string var = “Hello”;
```
5. Boolean:

	It is used to store logical values that can be either true or false.
	To print a boolean value threw a `cout` you need to add `boolalpha` unless 0 or 1 will be printed for 0 false and 1 true.
```
boolean var = false;
cout<<boolalpha<<var;
```
### 6. Arithmetic Operators:

1. The Addition (+) and The Subtraction (-) Operators:

	The addition operator is used to sum between two numbers or concatenate two strings while the subtraction operator is used to subtract numbers.
```
int a = 1;
int b = 2;
string str1 = “Hello ”;
string str2 = “world!!”;

int c = a+b;
string str12 = str1 + str2;
int c = b-a;
```
2. Incrementing/Decrementing Variables:

	To increment we use the `++` to increment by 1 and `+=` to increment by any number we like.
	To decrement we use the `--` to decrement by 1 and `-=` to decrement by any number we like.
```
int a = 1;
a++;
a+=2;
a--;
a-=2;
```
3. The Division (/) Operator:

	Used for mathematical division
	Notice that dividing two integers will give you the part before the reminder even if the result is stored in a double, this a logic error.
```
double b = 12/6;
	cout<<b;
```

4. The Modulo (%) Operator:

	Used to get the reminder of any division
```
double b = 12%6;
cout<<b;
```

5. The Multiplication (*) Operator:

	Used for multiplication between numbers
```
double b = 12*6;
cout<<b;
```
6.	Type Caste:

	To change a data type in a different data type you type in a parentheses the type of data you want to cast before writing the variable.
	We will use casting to solve the logic error mentioned before:
```
int a = 2;
int b = 3;

double c = (double) b/ a;
```


7. Printing Floating Point Numbers:

	The `cout` command is non-specific such it may lead to logic errors while printing such if there is a specific case such as printing floating point numbers called `printf`.
The `printf` command is a specific command such you need to specify the data type before printing.
`%f` stands for floating point numbers.
`%d` stands for integers.
```
int a = 2;
double b = 2.23;
printf(“%d \n”,a);
printf(“%f \n”,b);
```
### 7. Boolean Operators:

1. Equal To:

	`==` stands for equal to.

2. Not equal To:

	`!=` stands for not equal to.

3. Less Than:

	`<` stands for less than

4. Less Than or Equal to:

	`<=` stands for less than or equal to

5. Greater Than:

	`>` stands for greater than

6. Greater Than or Equal To:

	`>=` stands for greater than or equal to

7. The And Operator:

	The `&&` (and) operator allows for compound (more than one) boolean expressions.
	All boolean expressions must be true in order for the whole thing to be true. If at least one boolean expression is false, then the whole thing is false.

8. The Or Operator:

The `||` (or) operator allows for compound (more than one) boolean expressions. If at least one boolean expression is true, then the whole thing is true. To be false, all boolean expressions must be false.

9. The Not Operator:

	The `!` (not) operator produces the opposite result of the boolean expression that it modifies.
### 8.Conditional Statements:

1. The if-statement:

	Conditionals are pieces of code that make a decision about what the program is going to do next. The most common conditional is the if statement.
```
if(condition){
// Code to be executed if the condition is true
}
```
The condition is boolean expression that uses the operators discussed before.

2. The if-else Statement:

	The if-else statement checks to see if a condition is true, and then has specific actions that take place. However, it also provides a specific set of actions if the boolean expression is false. Use the else keyword to introduce the code to run when false is evaluated.
```
if(condition){
// Code to be executed if the condition is true
}

else{
// Code to be executed if the condition is false
}
```
3. The else-if Statement:

	The else if statement allows you to check for multiple conditions sequentially.
```
if(condition1){
// Code to be executed if the condition1 is true

}else if(condition2){
// Code to be executed if the condition2 is true

}else{
// Code to be executed if the condition1 and condition2 are false

}
```
4. Switch Statement:

	The switch case statement is a way to make a decision with multiple
possible outcomes. Instead of nesting or sequencing many if statements, C++ allows you to use the switch statement.
In the switch statement we will need to use “break” reserved word after each case and the “default” reserved” word as the final case.
```
switch (expression) {
case value1:
// Code to be executed if expression matches value1
break;

case value2:
// Code to be executed if expression matches value2
break;
// ...

default:
// Code to be executed if expression does not match any case
break;
}
```
### 9. Loops:

1. For Loop:

	For loop helps us to execute a block of code a fixed number of times.
	The header of the for-loop is made out of 3 parts:

	1. intializtion of the variable

	2. boolean expression

	3. updating the variable

	The logic of the for-loop is that that you initialize a variable you will use to loop till the boolean expression is false after updating the variable after each loop.
```
for (initialization expr; test expr; update expr){
// body of the loop
// statements we want to execute
}

int a = 4;
for(int i; i<a;i++){
cout<<”Hello”<<endl;
}
```
2. While Loop:

	While loop repeatedly executes a block of code till the given condition is true.
	The logic of the while loop is that it will keep on looping till the condition is false and that why we update the condition in loop so it changes after each loop.
```
while (condition){
// statements
update_condition;
}

int a = 4;
int i = 0;
while(i != a){
cout<<”Hello!!”<<endl;
i++;
}
```
3. Do-While Loop:

	Do-while loop also executes the block of code till the condition is true but the difference between a while and a do-while loop is that the do-while executes the code once without checking the condition and the test condition is tested at the end of the loop body.
The logic is the same as the while loop but the difference that the checking of expression happens after the loop not before.
```
do {
// Code to be repeated
update_condition;
} while (condition);

int a = 4;
int i = 0;
do{
cout<<”Hello!”<<endl;
i++;  
}while(i!=a);
```
Its important to note that the usage of each loop type will be based on the application you are doing.

### 10. Nesting:

In C++ you find a lot of cases where you need to use a condition statement inside and condition statement or a loop inside a loop this concept is nesting.
```
//the following code draws a 10x10 square made of "*".
for(int i = 0;i<10;i++){
	for(int j = 0;j<10;j++){
		cout<<"*";
	}
	cout<<endl;
}
```
