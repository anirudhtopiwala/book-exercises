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