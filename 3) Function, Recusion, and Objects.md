# **3rd Course: Function, Recursion, and Objects**

C++ is a high-level programming language. It was developed in 1983 by Bjarne Stroustrup at Bell Labs. It is used for developing various applications.


## 1. Functions

### - Definition:

A function in any programing language is a means to not repeat code every time we need that same code, so we just call it by function name.

To build a function we need to understand its structure.

### - Structure:

The function is made of a **header**, **parameters**, and a **body**.

**Header**: specifies return type, name, and parameters.

**Body**: contains the code we want to execute multiple times.

When the function doesn’t return anything we write void as return data type in the header.

We use parameters when they are needed only. A parameter can be a data type: int, float, vector, array….

It is important to note that in C++, the order of which the function is created and called is important. The best practice is to create the function above where you want to call it.

```
void PrintArray(string array[], int size) {
    for (int i = 0; i < size; i++)
        cout << array[i] << endl;
}
void Add(int num1, int num2) {// a function that uses the parameters
    cout << num1 + num2 << endl;
}
void GreetTwice() {// afunction that doesn't use parameters
    cout << "Hello" << endl;
    cout << "Hello" << endl;
}
int main() {
    GreetTwice(); // Executes the function
    return 0;
}
```

### - Exception Handling:

Exceptions are errors that happen at runtime meaning after the code started executing and the cause the whole system to crash. Hence handling exceptions that may occur is a most for the program to run  smoothly and safely.

We handle this using

```
try {
    // Code that might throw an error
    throw runtime_error("Error message");
} catch (runtime_error& e) {
    cout << e.what() << endl;
}

```

with the code inside the try{} with the addition to the program that checks if the error will be triggered.
```
void Divide(int num1, int num2) {
    try {
        if (num2 == 0)
            throw runtime_error("Cannot divide by zero.");
        cout << num1 / num2 << endl;
    } catch (runtime_error& e) {
        cout << e.what() << endl;
    }
}
```

### - Function Overloading:

When we need the same logic to be applied for multiple cases we can define multiple functions with the same name but different parameters.
```
void Add(int num1, int num2) {
    cout << num1 + num2 << endl;
}
void Add(int num1, int num2, int num3){
	cout << num1 + num2 + num3 << endl;
}
```

### - Variable Scope:

Variables have a cope to where they can be used.

A **local variable**, a local scope, is a variable declared inside a function and is only accessible there.
```
void MyFunction() {
    string message = "Hello";// message is a ocal variable
    cout << message << endl;
}
```
A **global variable**, a global scope, is a variable declared outside all functions and is accessible everywhere.
```
string greeting = "Hello";// greeting is local variable

void SayHello() {
    cout << greeting << endl;
}
```
It’s important to know that local variables override global ones within their scope.
```
string my_var = "global";

void PrintScope() {
    string my_var = "local";
    cout << my_var << endl; // Prints "local"
}
```

We use the `const` to prevent any modifications for our variables, and it’s mostly used for global variables.
```
const string kMyConstant = "Fixed Value";
```

### - Return Values:

Functions can return values to the caller, making them more versatile. The data type returned is the same as the one defined in the header.
```
int AddFive(int num) {
    return num + 5;
}
string Combine(string a, string b) {
    return a + b;
}
vector<int> MultiplyFive(vector<int>& nums) {
    vector<int> result;
    for (int n : nums)
        result.push_back(n * 5);
    return result;
}
```
### - Helper function:

Functions can call other built-in functions and your own defined functions to simplify the logic.
```
/**
* This function finds the radius of a circle given
* two coordinate points
*
* @param x1 A double of the first x-coordinate
* @param y1 A double of the first y-coordinate
* @param x2 A double of the second x-coordinate
* @param y2 A double of the second y-coordinate
* @return The radius of a circle in double
*/
double FindRadius(double x1, double y1, double x2, double y2) {
return(sqrt(pow(x2 - x1, 2) + pow(y2 - y1, 2)));
}
/**
* This function finds the area of a circle given
* two coordinate points
*
* @param x1 A double of the first x-coordinate
* @param y1 A double of the first y-coordinate
* @param x2 A double of the second x-coordinate
* @param y2 A double of the second y-coordinate
* @return The area of a circle in double
*/
double FindArea(double x1, double y1, double x2, double y2) {
return(M_PI * pow(FindRadius(x1, y1, x2, y2), 2));
}
int main() {
cout << FindArea(0.0, 0.0, 4.0, 4.0) << endl;
return 0;
}
```
## 2) Recursion
Some algorithms are neatly solved by calling for the same function several times until a certain condition is met, that what we call recursion.
Every recursive function must have two parts:
Base case: the condition that stops the recursion.
Recursive case: The part where the function calls itself with a modified argument. 
```
int Factorial(int n) {
    if (n <= 1) return 1;           // Base case
    else return n * Factorial(n-1); // Recursive case
}
int Fibonacci(int n) {
    if (n <= 1) return n; // Base case
    else return Fibonacci(n-1) + Fibonacci(n-2); // Recursive case
}
```
## 3) Objects:

To start with object oriented programing, we need to define a few things first:

**Class**: A blueprint that defines the structure and behavior of a type of object. It includes attributes (data) and methods (functions).

**Object**: An instance of a class. It holds actual data and can perform actions defined by the class, for simplicity you can consider it a reserved place in memory that can be created to handle and hold the info about the class.

**Instantiation**: The process of creating an object from a class.

**Instance**: A specific object created from a class.

## 4) Mutability

**Definition**: Objects are mutable, meaning their attributes can change after creation.

Example: A Player class with attributes like health, score, and level—all of which can be updated during gameplay.


## 5) External Functions

Purpose: Promote code reusability and cleaner structure.

Function Example: PrintPlayer(Player p) prints the player’s current status.

Challenge: External functions like ChangeHealth(Player p, int amount) don’t permanently alter the object’s state because they pass by value, not by reference.

Limitation

Changes made inside external functions are not retained outside the function scope.

This highlights the need for class member functions or passing by reference to make persistent changes.

External functions are useful for organizing code, but they have limitations when it comes to modifying object state.
````
#include <iostream>
using namespace std;
//add class definitions below this line
class Player {
	public:
		int health;
		int score;
		int level;
	Player() {
		health = 100;
		score = 0;
		level = 1;
	}
};
//add class definitions above this line
//add function definitions below this line
void PrintPlayer(Player p) {
	if (p.health <= 0) {
		cout << "This player is dead. They died on level " <<
		p.level;
		cout << " with a score of " << p.score << "." << endl;
		} else {
			cout << "This player has " << p.health << " health, a score of " << p.score;
			cout << ", and is on level " << p.level << "." << endl;
		}
}
void ChangeHealth(Player p, int amount) {
p.health += amount;
cout << "New health = " << p.health << endl;
}
//add function definitions above this line
int main() {
	//add code below this line
	Player player1;
	PrintPlayer(player1);
	player1.health = 0;
	player1.score += 25;
	player1.level += 1;
	PrintPlayer(player1);
	ChangeHealth(player1, 20); //changes health of player1
	PrintPlayer(player1); //does not register changes from
	ChangeHealth function
	//add code above this line
	return 0;
}
````

## 6) Functions

Definition: Functions defined inside a class that can directly access and modify private attributes.

Syntax: Declared within the class and called using dot-notation (e.g., player.ChangeHealth(25)).

Advantage: Unlike external functions, class functions preserve changes to object state.

Class functions are the preferred method for modifying object data in C++.

They enforce encapsulation, improve code clarity, and ensure changes persist.

External functions were a steppingstone to understanding mutability—but class functions are the real deal.
````
#include <iostream>
#include <vector>
using namespace std;
//add class definitions below this line
class Meal {
	public:
		void AddDrink(string drink) {
		drinks.push_back(drink);
}
void PrintDrinks() {
	for (auto a: drinks) {
	cout << a << endl;
	}
}
void AddAppetizer(string app) {
	appetizers.push_back(app);
}
void PrintAppetizers() {
	for (auto a: appetizers) {
	cout << a << endl;
	}
}
void AddMainCourse(string mc) {
	main_courses.push_back(mc);
}
void PrintMainCourses() {
	for (auto a: main_courses) {
	cout << a << endl;
	}
}
void AddDessert(string dessert) {
	desserts.push_back(dessert);
}
void PrintDesserts() {
	for (auto a: desserts) {
	cout << a << endl;
	}
}
private:
	vector<string> drinks;
	vector<string> appetizers;
	vector<string> main_courses;
	vector<string> desserts;
};
//add class definitions above this line
int main() {
//add code below this line
	Meal dinner;
	dinner.AddDrink("water");
	dinner.PrintDrinks();
	dinner.AddAppetizer("bruschetta");
	dinner.PrintAppetizers();
	dinner.AddMainCourse("roast chicken");
	dinner.PrintMainCourses();
	dinner.AddDessert("chocolate cake");
	dinner.PrintDesserts();
	//add code above this line
	return 0;
}
````

## 7) Class
A **class** is like a blueprint for creating objects. It defines what attributes (data) and behaviors (functions) an object will have. Think of it as a custom datatype that bundles everything related to a concept like a `Person`, `Phone`, or `Robot`.
It have the syntax:
````
class ClassName {
public:
    // public members (accessible from outside)
    
private:
    // private members (hidden from outside)
};
private and public will be expalined later on
````
Person Class:
````
class Person {
public:
    string name;
    int age;

    void SayHello() {
        cout << "Hello!" << endl;
    }
};

int main() {
	Person p1;
	p1.name = "Ali";
	p1.age = 22;
	p1.SayHello(); // Outputs: Hello!
}
````
An important part of the Class is the constructor.
A **constructor** is a special function that runs automatically when you create an object. It’s used to initialize attributes and set up the object’s state. Think of it as the “setup crew” that gets everything ready behind the scenes.
it have the syntax:
````
class Person {
public:
    string name;
    int age;

    // Constructor
    Person(string n, int a) {
        name = n;
        age = a;
    }
};
int main() {
	Person p1("Ali", 22);
}
````

