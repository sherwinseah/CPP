# C++

## Running C++ Files 
Run file on terminal, output written to a.out

```
$ g++ hello.cpp
```

Read output file information
```
$ ./a.out
```

Run file on terminal, definining the output file name as "hello"
```
$ g++ hello.cpp -o hello
```

## Variables
Variable declaration
```
int score;
```

Variable assignment
```
score = 0;
```

Combining variable declaration and assignment
```
int score = 0;
```

Print variable to screen using Chaining
```
std::cout << score << "\n"; 
```

Take in user input
```
double tip;
std::cout << "Enter tip amount: "    // std:: is used because string and vector are in C++ standard library and belongs to std namespace
std::cin >> tip;
```

Basic data types
int, double, char, string (used as std::string), bool

Datatype modifiers - used with built in data types to modify length of data a particular data type can hold
signed, unsigned, short, long

Constant variables cannot be changed by the program during execution
```
const double quarter = 0.25;
```

Type casting, uses notation "(type) value", which means 'convert value to type'
```
double weight1;
int weight2;
weight1 = 15.6;
weight2 = (int) weight1; // changes weight2 to 15, double to int removes the decimal without rounding
```

Sample full program
```
// This program outputs the message "Hello World!" to the monitor 
#include <iostream> //pre-processor directive, locate file that contains the code for a library.
// iostream contains code that allows for input and output such as displaying data in the terminal window or reading input from keyboard

int main() { //main function required for all C++ programs

   std::cout << "Hello World!\n"; // cout is used to send text to the terminal

   return 0; // return used to end function, optional

}
// compiler ignores all the white spaces except those concerning if statements. 
```

## Conditionals Operators
If-else if-else statement
```
if (condition) {
    do something
} else if (condition) {
    other code
} else {
    other final code
}
```

Switch statement - better handling of multiple outcomes
```
int main() {
  
  int number = 2;
  
  switch(number) {
    case 1 :
      std::cout << "Bulbusaur\n";
      break; // break required for switch statement otherwise the code would execute all subsequent cases even after finding a match
    case 2 :
      std::cout << "Ivysaur\n";
      break;
    case 3 :
      std::cout << "Venusaur\n";
      break;
    default :
      std::cout << "Unknown\n";
      break; 
  }
}
```

## Logical Operators
- and &&
- or ||
- not !

## Loops
While loop
```
while (condition) {
    do something
}
```
For loop
```
for (int i=0; i<10; i++;){ // (initialization of counter, continue condition, change in counter)
    do something
}
```

## Errors
Syntax errors
- Missing semicolon, closing parenthesis, brackets
Type errors
- Forgetting to declare variable, storing value into wrong type
Link-time errors
- Linker takes separate files and combines them into a single exe
- Using a function that was never defined
- Writing Main() instead of main()
Run-time errors
- Errors where computer is asked to do something it cant reliably do
- Division by zero error, trying to open a file that doesnt exist
Logic errors
- Program logic is flawed, silly mistakes in if statement or loops

## Vector 
A sequence of elements that can be accessed by index
Initializing vector
```
#include <iostream>
#include <vector> // preprocess directive to tell compiler to include standard vector library

int main() {
  std::vector<double> subway_adult; // std::vector<type> name;
  std::vector<double> location = {42.651443, -73.749302}; //initialize vector with specific values
  std::vector<double> ranbow_colors(7); // initialize vector with presizing, setting size of vector, 0.0 is the default value for double
  std::cout << location[0] << "\n"; // notation vector[index] to access element
}
```
Adding and removing elements in the vector
```
#include <iostream>
#include <vector>

int main(){
    std::vector<std::string> dna = {"ATG", "ACG"};
    dna.push_back("GTG"); // add elements to index 2
    dna.pop_back(); // remove elements from the back, no return value
}
```
<std::vector> not only stores elements but also the size of the vector
- vector.size() returns size of vector

## Arrays
- Similar to vectors, used to store sequential collection of elements but size cannot be changed
```
int favoriteNums[4]; // specifying size of an int array
int favouriteNums[] = {1, 2, 3, 4}; // initialize array with custom values upfront, auto have size of 4
favouriteNums[0] = 5; //modifies array at index 0
```

## Functions
- By including headers like <math> or <string>, we gain access to helpful functions
- eg. #include <math> gives access to the function sqrt() 
- You can create your own functions; comprised of 2 distinct parts: Declaration (function name, return type, parameters for input), and Definition (body of the function, instruction of what the function is supposed to do)   
```
return_type function_name(any, input, parameters){
    // code block
    return output_if_any;
}
```
Example:
```
void make_sandwich() { // void function means there is no type, also known as a subroutine, returns no value
    std::cout << "bread\n"; 
    std::cout << "egg\n";
    std::cout << "avocado\n";  
    std::cout << "bread\n"; 
}

int main() {
  make_sandwich();
}
```
- Most data types can be returned, including double, int, bool, char, std::string, std::vector
```
#include <iostream>

bool needs_it_support() { // functions with return other than void requies value returned of the same type
  bool support;

  std::cout << "Hello. IT. Have you tried turning it off and on again? Enter 1 for yes, 0 for no.\n";
  std::cin >> support;

  return support;
}

int main() {
  std::cout << needs_it_support();
}
```
- Parameters are used in a function's definition, acting as placeholders for input values
- Can have multiple parameter but must remember the order when you call the function
- Function call must have the same number of arguments as parameters, where arguments are passed in the same order
```
#include <iostream>

void name_x_times(std::string name, int x){
  while (x > 0){
    std::cout << name;
    x -= 1;
  }
}

int main() {
  std::string my_name = "Win!";
  int some_number = 5;
  name_x_times(my_name, some_number);
}
```
### Flexibility and Scope of functions
- variables defined in global scope are accessible throughout the program
- Variables defined in a function have local scope and only accessible inside the function
- Multi-file programs (Using separate .cpp files)
    - Move function definitions (codes) into specialized .cpp files
        ```
        double average(double num1, double num2) {
            return (num1 + num2) / 2;
            }
        ```
    - Have declaration above the main()
        ```
        double average(double num1, double num2);
        ```
    - main() program will know about the funciton definition when it compiles as it links together any files in the compilation statement into a single executable
    - Programs with multiple .cpp files need to be linked at compile time
        ```
        g++ main.cpp my_additional_functions.cpp
        ```
- Multi-file programs (Using additional .h file)
    - Move function declarations into a header file with the extension .hpp or .h. 
    - Good for reducing the need for declaring multiple functions in different files
        ```
        #include "my_function.hpp"
        ```
- Getting the functions inline i.e inline functions
    - inline keyword advises computer to insert function's body where the function call is. Can help with execution speed but may hinder execution speed.
        ```
        inline
        ```
    - Should always add the inline keyword if you are inlining functions in a header, except member functions
        ``` 
        inline //in .hpp file
        std::string goodnight1(std::string thing1) {
        return "Goodnight, " + thing1 + ".\n";
        }
        ```
- Pre-filling arguments for default arguments
    - Default arguments can be added to function declarations
        ```
        void intro(std::string name = "Win");
        ```
- Function overloading
    - Allowing function to accept an argument that can either be int or double
    - Want some function parameters to be optional
    - Give multiple C++ function the same name, as long as at least 1 condition is true
        - Each has different type parameters
        - Each has different number of parameters
    - Overloading allows us to change the way a function behaves depending on what is passed in as an argument
    - If function has same body but different input, it is easier to use templates. Template is C++ tool that allows programmers to add data types as parameters. 
        - std::string and std::vector are an examples of templates
        - Templates are entirely created in header files
        - Templates let us choose the type implmenetation right when you call the function
        ```
        template <typename T>
        T get_smallest(T num1, T num2) {
            return num2 < num1? num2 : num1;
        }
        ```
        - Using templates slow down program's compile time but speeds up execution time
        - Works as long as the type can be used with the methods expected
- Globality of variables
    - fns.cpp
        ```
        int x = 5;
        ```
    - fns.hpp
        ```
        extern int x;
        ```
    - main.cpp
        ```
        #include <iostream>
        #include "fns.hpp"

        int main() {
            std::cout << x;
            return x;
        }
        ```
    - Execute:
        ```
        g++ main.cpp fns.cpp
        ```

## Classes and Objects
- Class serves as a blueprint for objects which are instances of the class
- Object gets characteristics and behaviors from its class
```
class City {      // Empty C++ class

};                // semicolon is required at the end of the class
```
### Class members
- Components of a class are called class members. Eg. string's length using str1.length(), class members can be accessed using object.class_member
- Two types of class members
    - Attributes also known as member data, consist of information about an isntance of the class
    - Methods, also known as member functions, are functions that can use with an instance of the class
```
class City {
  // attribute
  int population;

public:
  // method
  void add_resident() {
    population++;
  }
};
```
Example:
- song.hpp
    ```
    #include <string>

    class Song {  // by default, everything in a class is private
        std::string title;

    public:  // everything below this is public
        void add_title(std::string new_title);

        std::string get_title();
    
    private: // used to define things you want below public to be private as well
        bool top_hits;

    };
    ```
- song.cpp
    ```
    #include "song.hpp"

    void Song::add_title(std::string new_title){
        title = new_title;
    }

    std::string Song::get_title(){
        return title;
    }
    ```
- music.cpp
    ```
    #include <iostream>
    #include "song.hpp"

    int main() {
        Song electric_relaxation;
        electric_relaxation.add_title("Electric Relaxation");
        std::cout << electric_relaxation.get_title();
    }
    ```
### Constructors
- Special kind of method that lets you decide how objects of a class are created
- Has the same name as the class and no return type
- Shine when you want to instantiate object with specific attributes
Example:
- song.hpp
    ```
    #include <string>

    class Song {
        std::string title;
        std::string artist;

    public:
        Song(std::string new_title, std::string new_artist); // Constructor
        std::string get_title();
        std::string get_artist();
        
    };
    ```
- song.cpp
    ```
    #include "song.hpp"

    //Method one of adding constructor
    Song::Song(std::string new_title, std::string new_artist)
        : title(new_title), artist(new_artist) {}

    // Method two of adding constructor
    Song::Song(std::string new_title, std::string new_artist){
        title = new_title;
        artist = new_artist;
    }

    std::string Song::get_title() {
        return title;
    }

    std::string Song::get_artist() {
        return artist;
    }
    ```
- music.cpp
    ```
    #include <iostream>
    #include "song.hpp"

    int main() {
        Song back_to_black("Back to Black", "Amy Winehouse");
        std::cout << back_to_black.get_title() << "\n";
        std::cout << back_to_black.get_artist() << "\n";
    }
    ```
### Destructors
- For tidying up and preventing memory leaks by destroying objects
- Usually not needed to be called, since automatically called when
    - Object moves out of scope
    - Object is explicityly deleted
    - When program ends
Example:
- song.hpp
    ```
    public:
        ~City();
    ```
- song.cpp
    ```
    Song::~Song(){
        // any final cleanup
    }
    ```


