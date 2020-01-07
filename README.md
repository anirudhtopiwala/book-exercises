## Accelerated C++ Notes

**Other Solutions can be found [here](http://mathalope.co.uk/accelerated-c-solutions/)**

**1) Chapter 0 - Getting Started**



*   Angle brackets (<>) is used to call standard libraries.
*   In main(), a return of 0 means success and any other value means failure. 
*   Std::endl is a manipulator and the operator << does what the manipulator asks it todo.. Therefore whenever we use endl, the lines terminated and we move on to the next line. 
*   There are only three things in c++ that is not in free form. (meaning irrespective of spacing)
    *   String literals (anything between “ ” )
    *   '#' include name
    *   // comments

* Use /*     */ for comments across several lines.
*   A return may automatically be added in main function if not specified, but it is a good practice to mention is explicitly.

**2) Chapter 1 - Working with Strings**
* When a String is initilaized without value, it by defaults has empty or null value. 
*   Objects are part of the computers memories with a definite type. Variables are objects with names. 
*   When using Cin, the output gets stored in a buffer. It is important to keep a track of this and flush the buffer as needed, otherwise it may happen that the some values may stay inside the buffer for significant portion of time. 
*   A variable is deleted and the memory is freed as soon as the scope in which variable is defined ends. 
*   For nested scopes, two const variables with same names can be declared. [See this](http://mathalope.co.uk/2014/06/21/accelerated-c-solution-to-exercise-1-4/)
*   All local variables defined at the outer scope level may be seen/used by the inner scopes (at all levels). (vice versa not true)
*   **Cin is irrespective of spaces.. Meaning it will disregard any space given before the  input. Once it encounter space after a character entry it will store that in the buffer for future use.**
    *   **Eg: ```cin=  “   j   k  l “ ```will give ‘j’ as output when cout is called  and store ‘k’ and ‘l’ in its buffer. Next time cin is called, it will automatically take k and so and so on.**
*   **Two string literals cannot be concatenated: that is ```“hello” + “World” ```is an invalid operation. Although a string and a string literal can be concatenated.**
    *   Eg:
    ```
    string name = “world”
	cout<< “hello” + name<<endl (this is valid)
    Again   cout<< “hello” +” “ + name<<endl (this is not  valid)
    ```
**3) Chapter 2 - Looping and Counting**
*   ```Std::string:size_type``` should be used to store length of **strings**. This is because then the input string can have indefinitie length. If using int then memory may come up short. 
* ```Std::string:size_type``` is unsigned type. i.e it cannot store negtive values
* size_t is unsigned intergal type to hold size of any object in compiler. See [this](https://www.geeksforgeeks.org/size_t-data-type-c-language/)

**3) Chapter 3 - Working with Batches of Data**
* setprecision is of header <iomanip> and is only for stream.
* using double is almost always the right choice instead of float on modern computers. Float can only handle 6 compared to 15 significant digits of double.
* standard datatypes (int, double) has no intialization value and therefore should always be intiilaized. String is intiilaized to null or empty by default.
* typedef scopes is similar to the varible being declared. It is used to rename the definition of a type
* typename is used to indicate that the following argument is a type and not a variable. This is required by compiler to parse the program when compiling. This process is called name lookup. If not done then the compiler can store the typeame in internal buffer and while running can give errors if type is being incorrectly used. 
* template is used for working with different data types.
* sort is defined in <algorithm>

**3) Chapter 4 - Organizing programs and data**
* you can use "throw std::domain_error" to report if something goes wrong. It is included using <stdexcept>. It can also contain an error message like "something went wrong"
* Whike making functions you should not pass variables by reference if thinking of using sort and similar functions that will affect the original variable.
* 

**Inheritance Pointers**
* Multiple Inheritance is a feature of C++ where a class can inherit from more than one classes.
* The constructors of inherited classes are called in the same order in which they are inherited.
* **The Diamond Problem** : the diamond problem occurs when two superclasses of a class have a common base class. exmaple: class A; class B inhereits from A, class C inherits from A, and D inherits from B and C. In this case constructor of A is called twice and caused ambiguity in variables of class A. To solve this problem **virtual** keyword used while inhereting. Therefore, class B : virtual class A; class C : virtual class A. This way the **deafult constructor** of class A is called only once and no ambiguity. To call the paramterized constructor, the exception is to call the gradfather class paramter constructor in class D in intializer list as
```
class D(int x) : public B(x), c(x), A(x) {}
```
* A base class pointer can point to a derived class object, but we can only access base class member or virtual functions using the base class pointer.
* If a derived class writes its own method, then all functions of base class with same name become hidden, even if signaures of base class functions are different. In the above question, when fun() is rewritten in Derived, it hides both fun() and fun(int) of base class.
* We can access base class functions using scope resolution operator even if they are made hidden by a derived class function.

**Virtual Functions**
* Rules for Virtual Functionsy6
    *    Virtual functions cannot be static and also cannot be a friend function of another class.
    * Virtual functions should be accessed using pointer or reference of base class type to achieve run time     polymorphism.
    * The prototype of virtual functions should be same in base as well as derived class.
    * They are always defined in base class and overridden in derived class. It is not mandatory for derived class to override (or re-define the virtual function), in that case base class version of function is used.
    * A class may have virtual destructor but it cannot have a virtual constructor.
* A pure virtual function can also have a body which can be called by using the qualified name. Exapmpl A::func() where func is pure virtual, but here will act as a normal function.
* Any virtual method in base class is called according to the type of object being referred or pointed, rather than the type of pointer or reference. 
*  We can have pointers or references of abstract classes but they cannot have objects.
*  **When a class has a virtual function, functions with same signature in all descendant classes automatically become virtual.**
*  


**Google C++ Style Guide:**
**Includes**
* hpp header files explicitly mean that they are mean for c++ and not for c. The compiler does not care though. The norm is used to .h, which will be common to both.
* You should include the #define guard to prevent multiple inclusions.
* You should not use inline if function greater than 10 lines. For and switch statement functions should be avoided for inline. 
**Scoping**
* Unnamed name spacing can be useful to avoid collision during runtime. But never use unnamed name pace in header files. 
* Namespace should start immediately after includes and should always end with the comment "End of name space"
* Prefer grouping functions with a namespace instead of using a class as if it were a namespace.
**Naming**
* File names should be in small letters and word can be separated by '_' or '-'
* All classes, structs, type aliases, enum,etc are named by starting each word with a capital letter, no spaces and no '_'. Eg: MyFirstClass
* Variables are all in small and underscore separating the words if needed. Data members of the class have trailing underscores. eg: a_local_variable, a_class_data_member_
* Struct data members dont have trailing underscores.
* global variables can be started with g_
* variables that are marked constant should be with a leading "k" and then a mixed case. eg: const kDaysInAWeek
* Functions have a mixed case aka upper camel case. No underscores, make acronyms as one word. Eg: DeleteUrl()
* Namespace names are all lowercase. 
* The top level namespace is usually the name of the project or the subdirectory.
*
**General**
* Avoid calling virtual functions in constructor
* Initializing const variables in constructor is good. 
* Never do implicit data type conversions. 
* All parameters passed by reference must be labeled const.
* input arguments in a function are values or const references while output arguments are pointers. Input parameters may be const pointers if needed.
