# 4th Course: Inheritance and Encapsulation

C++ is a high-level programming language. It was developed in 1983 by Bjarne Stroustrup at Bell Labs. It is used for developing various applications.

## Encapsulation

### 1) Definition:

Encapsulation is all about bundling related data and functions together inside a class and then controlling how that data is accessed or modified. Think of it like putting your valuables in a safe: you decide who gets the key and what they can do with it.

In C++, we use **access modifiers** like public and private to manage this control:

-   **public:** accessible from anywhere
-   **private**: accessible only within the class
````
class  ExampleClass  {
 public:
	void SetN(int n1, int n2) {
	  num1 = n1;
	  num2 = n2;
	} 
	void Describe() {
		cout << "My numbers are: "  << num1 << " and "  << num2 << endl;
	} 
	int Sum() { 
		return  num1 + num2; 
	} 
private: 
	int  num1;
	int  num2;
};
//`num1` and `num2` are private attributes
// You can't touch them directly from outside the class but you can interact with them through public methods like `SetN`, `Describe`, and `Sum`
````
### 2) Getters and Setters
So now that we’ve locked down our data using `private`, how do we actually _use_ it? That’s where **getters** and **setters** come in.

A **getter** (or accessor) is a public function that lets you _read_ a private attribute. It’s like peeking inside the safe without being able to touch anything.
````
class Phone {
public:
    Phone(string mo, int s, int me) {
        model = mo;
        storage = s;
        megapixels = me;
    }

    string GetModel() {
        return model;
    }

private:
    string model;
    int storage;
    int megapixels;
};

int main() {
	Phone my_phone("iPhone", 256, 12);
	cout << my_phone.GetModel() << endl; // Outputs: iPhone
}
````
A **setter** (or mutator) is the flip side of a getter, it lets you _change_ a private attribute, but only in a controlled way.
````
class Phone {
public:
    Phone(string mo, int s, int me) {
        model = mo;
        storage = s;
        megapixels = me;
    }
	void SetModel(string new_model) {
	    model = new_model;
	}

	string GetModel() {
        return model;
    }

private:
    string model;
    int storage;
    int megapixels;
};

int main() {
	Phone my_phone("iPhone", 256, 12);
	cout << my_phone.GetModel() << endl; // Outputs: iPhone
	my_phone.SetModel("XR");
	cout << my_phone.GetModel() << endl; // ✅ Outputs: XR
}
````

### 3) Data Validation
Data validation is when we set certain rules that applies to the updatable or changeable data in our program and it depends on the functionality of our code.
````
class Person {
public:
    Person(string n, int a) {
        name = n;
        age = a;
    }

    void SetAge(int new_age) {
        if (new_age >= 0 && new_age <= 100) {// here we data falidate the age since we cant really find people with an age of -100
            age = new_age;
        }
    }

    int GetAge() { return age; }

private:
    string name;
    int age;
};
int main() {
	Person my_person("Calvin", 6);
	my_person.SetAge(-100); // Won’t update age
}
````

## Inheritance

### 1) Definition
Inheritance allows one class (called the **derived class**) to inherit attributes and methods from another class (called the **base class**). It’s like saying, “This new class is a specialized version of that old one.”

We also call the base class **base class** and the derived class **child class**.
````
//Parent Class
class Person {
public:
    string name;
    int age;

    Person(string n, int a) {
        name = n;
        age = a;
    }

    void SayHello() {
        cout << "Hello!" << endl;
    }
};

//Child Class
class Superhero : public Person {
public:
    string secret_identity;

    Superhero(string n, int a, string s) : Person(n, a) {
        secret_identity = s;
    }

    void RevealSecretIdentity() {
        cout << "My real name is " << secret_identity << endl;
    }
};
int main() {
	Superhero hero("Bruce", 35, "Batman");
	hero.SayHello();// Inherited from Person
	hero.RevealSecretIdentity();// Defined in Superhero
}
````
Notice how we used `Person(n, a)` inside the `Superhero` constructor? That’s how we pass values to the base class constructor. It ensures the base part of the object is properly initialized.

### 2) Extending
When you extend a class, you add new attributes or methods to the derived class without touching the base class. This keeps your code modular and flexible.
````
class Person {
public:
    string name;
    int age;

    Person(string n, int a) {
        name = n;
        age = a;
    }

    void SayHello() {
        cout << "Hello!" << endl;
    }
};

class Superhero : public Person {
public:
    string nemesis;

    Superhero(string n, int a, string ne) : Person(n, a) {
        nemesis = ne;
    }

    void SayNemesis() {
        cout << "My nemesis is " << nemesis << endl;
    }
};
````
Now `Superhero` has everything `Person` has plus its own `nemesis` and a new method `SayNemesis()`.

### 3) Overriding
Sometimes, you want to **change** how a method behaves in the derived class. That’s called **overriding**.
Back to our superhero example, Let’s say you want `SayHello()` to sound more heroic.
````
class Person {
public:
    string name;
    int age;

    Person(string n, int a) {
        name = n;
        age = a;
    }

    void SayHello() {
        cout << "Hello!" << endl;
    }
};

class Superhero : public Person {
public:
    string nemesis;

    Superhero(string n, int a, string ne) : Person(n, a) {
        nemesis = ne;
    }

    void SayNemesis() {
        cout << "My nemesis is " << nemesis << endl;
    }
    void SayHello() {
	    cout << "My name is " << name << ", and criminals fear me." << endl;
	}
};

int main() {
	Superhero hero("Bruce", 35, "Batman");
	hero.SayHello();// overridden version
	hero.Person::SayHello(); // Calls the base version
}
````
### 4) Multilevel Inheritance
#### Definition
Multilevel inheritance means a class inherits from another derived class, which itself inherits from a base class.
````
class A {
public:
    void ShowA() {
        cout << "Class A" << endl;
    }
};

class B : public A {
public:
    void ShowB() {
        cout << "Class B" << endl;
    }
};

class C : public B {
public:
    void ShowC() {
        cout << "Class C" << endl;
    }
};
int main() {
	C obj;
	obj.ShowA(); // From A
	obj.ShowB(); // From B
	obj.ShowC(); // From C
}
````
So why we use such a complicated concept, well that is because:
-   **Layered abstraction**: Each class adds its own behavior
-   **Code reuse**: No need to duplicate shared logic
-   **Scalability**: You can keep extending without rewriting

## Polymorphism
### 1) Definition
Polymorphism lets you use a **base class pointer or reference** to interact with derived class objects. The magic happens when you override methods in the derived class and call them through the base class then C++ figures out which version to use at runtime.

We use polymorphism because:
- We can write flexible, reusable code
- We  can treat different objects uniformly
- We can extend behavior without changing existing logic
````
class Animal {
public:
    void Speak() {
        cout << "Animal sound." << endl;
    }
};

class Dog : public Animal {
public:
    void Speak() {
        cout << "Woof!" << endl;
    }
};

class Cat : public Animal {
public:
    void Speak() {
        cout << "Meow!" << endl;
    }
};

int main() {
	Dog d;
	Cat c;
	d.Speak(); // Woof!
	c.Speak(); // Meow!
	Animal* a1 = &d;
	Animal* a2 = &c;
	a1->Speak(); // Outputs: Animal sound.
	a2->Speak(); // Outputs: Animal sound.

}
````
### 3) Virtual Function
To make polymorphism work, mark the base method as `virtual`:
````
class Animal {
public:
    vitual void Speak() {
        cout << "Animal sound." << endl;
    }
};

class Dog : public Animal {
public:
    void Speak() {
        cout << "Woof!" << endl;
    }
};

class Cat : public Animal {
public:
    void Speak() {
        cout << "Meow!" << endl;
    }
};

int main() {
	Dog d;
	Cat c;
	d.Speak(); // Woof!
	c.Speak(); // Meow!
	Animal* a1 = new Dog();
	Animal* a2 = new Cat();
	a1->Speak(); // Woof!
	a2->Speak(); // Meow!
// C++ dynamically chooses the correct method based on the actual object type. That’s **runtime polymorphism**.
}
````
## Advanced Object-Oriented
### 1) The Substitution Principle
This principle says: **if a class** `B` **is derived from class** `A`**, then you should be able to use an object of type** `B` **wherever an object of type** `A` **is expected.**

In practice, this means base class pointers or references should work seamlessly with derived class objects, as long as the derived class behaves like the base.
````
class Animal {
public:
    virtual void Speak() {
        cout << "Animal sound." << endl;
    }
};

class Dog : public Animal {
public:
    void Speak() override {
        cout << "Woof!" << endl;
    }
};

void MakeItSpeak(Animal* a) {
    a->Speak();
}

Dog d;
MakeItSpeak(&d); // Outputs: Woof!
````
This works because `Dog` is substitutable for `Animal`.

### 2) Abstract Classes and Pure Virtual Functions
Sometimes you want a class that only serves as a **template** but you don’t want to create objects from it directly. That’s where **abstract classes** come in.
An abstract class has at least one **pure virtual function**:
````
class Shape {
public:
    virtual void Draw() = 0; // Pure virtual
};
// Any class that inherits from `Shape` must implement 'Draw()`:
class Circle : public Shape {
public:
    void Draw() override {
        cout << "Drawing a circle." << endl;
    }
};

int main() {
	//Shape s; // Error
	Shape* s = new Circle(); // Works
	s->Draw(); // Outputs: Drawing a circle
}
````

We use this Abstract Class, well because:
-   **Enforce structure**: All derived classes must implement key behaviors.
-   **Enable polymorphism**: You can treat different objects uniformly.
-   **Design clean APIs**: Abstract classes define what must be done, not how.
