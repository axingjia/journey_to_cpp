# C++

* Geekforgeek Reference: https://www.geeksforgeeks.org/c-plus-plus/

# MY: Preface:
The structure is this repo is to store all the useful information. It will skip any unrelevant information or information that I personally don't find useful.

## 1. Setting up C++ Development
* C++ Compiler: GNU GCC for linux
* Command for compiling: 

        g++ filename.cpp -o any-name

        ex: 
        g++ helloworld.cpp -o hello

* command to run the compiled binary:

        ./hello

* For Windows installation, one popular IDE is Code: Blocks. Refer to here: https://www.codeblocks.org/downloads/binaries/
* For Mac, download Xcode

## 2. Writing First C++ Program – Hello World Example
SKIM

## 3. Is it fine to write void main() or main() in C/C++?
* void main() is illegal


        This is illegal
        void main(){
        // Body
        }

* It should always be int main(){}

## 4. C++ Data Types

        Data Type	Size (in bytes)	Range
        short int	2	-32,768 to 32,767
        unsigned short int	2	0 to 65,535
        unsigned int	4	0 to 4,294,967,295
        int	4	-2,147,483,648 to 2,147,483,647
        long int	4	-2,147,483,648 to 2,147,483,647
        unsigned long int	4	0 to 4,294,967,295
        long long int	8	-(2^63) to (2^63)-1
        unsigned long long int	8	0 to 18,446,744,073,709,551,615
        signed char	1	-128 to 127
        unsigned char	1	0 to 255
        float	4	 
        double	8	 
        long double	12	 
        wchar_t	2 or 4	1 wide character

## 5. Basic Input / Output in C++
* isostream: iostream stands for standard input-output stream. This header file contains definitions of objects like cin, cout, cerr, etc.
* iomainp: iomainip stands for input-output manipulators. The methods declared in these files are used for manipulating streams. The file contains definitions of **setw, setprecision**, etc
* fstream: This header file mainly describes the file stream. This header file is used to handle the data being read from a file as input or data being written into the file as output.

* **Un-buffered standard error stream (cerr)**: The C++ cerr is the standard error stream that is used to output the errors. This is also an instance of the iostream class. **As cerr in C++ is unbuffered so it is used when one needs to display the error message immediately. It does not have any buffer to store the error message and display it later**.
* **buffered standard error stream (clog)**: This is also an instance of ostream class and used to display errors but unlike cerr the error is first inserted into a buffer and is stored in the buffer until it is not fully filled, or the buffer is not explicitly flushed **(using flushed())**. The error message will be displayed on the screen too.

## 6. What happen when we exceed valid range of built-in data types in C++?


        // C++ program to demonstrate
        // the problem with 'char'
        #include <iostream>
        
        using namespace std;
        
        int main()
        {
            for (char a = 0; a <= 225; a++)
                cout << a;
            return 0;
        }

* a is declared as char. Here the loop is working from 0 to 225. So, it should print from 0 to 225, then stop. But it will generate a infinite loop. The reason for this is the valid range of character datatype is -128 to 127. When ‘a’ become 128 through a++, the range is exceeded and as a result the first number from negative side of the range (i.e. -128) gets assigned to a. As a result of this ‘a’ will never reach at point 225. so it will print the infinite series of character.


        // C++ program to demonstrate
        // the problem with 'bool'
        #include <iostream>
        
        using namespace std;
        
        int main()
        {
            // declaring Boolean
            // variable with true value
            bool a = true;
        
            for (a = 1; a <= 5; a++)
                cout << a;
        
            return 0;
        }

* This code will print ‘1’ infinite time because here ‘a’ is declared as ‘bool’ and it’s valid range is 0 to 1. And for a Boolean variable anything else than 0 is 1 (or true). When ‘a’ tries to become 2 (through a++), 1 gets assigned to ‘a’. The condition a<=5 is satisfied and the control remains with in the loop. See this for Bool data type.


*  short is short for short int. They are synonymous. **short, short int, signed short, and signed short int** are all the same data-type. 

        // C++ program to demonstrate
        // the problem with 'short'
        #include <iostream>
        
        using namespace std;
        
        int main()
        {
            // declaring short variable
            short a;
        
            for (a = 32767; a < 32770; a++)
                cout << a << "\n";
        
            return 0;
        }


* Will this code print ‘a’ till it becomes 32770? **Well the answer is indefinite loop,** because here ‘a’ is declared as a short and its valid range is **-32768 to +32767**. When ‘a’ tries to become 32768 through a++, the range is exceeded and as a result the first number **from negative side of the range(i.e. -32768) gets assigned to a**. Hence the condition “a < 32770” is satisfied and control remains within the loop.


        // C++ program to demonstrate
        // the problem with 'unsigned short'
        #include <iostream>
        
        using namespace std;
        
        int main()
        {
            unsigned short a;
        
            for (a = 65532; a < 65536; a++)
                cout << a << "\n";
        
            return 0;
        }

* Will this code print ‘a’ till it becomes 65536? **Well the answer is indefinite loop, because here ‘a’ is declared as a short and its valid range is 0 to +65535**. When ‘a’ tries to become 65536 through a++, the range is exceeded and as a result the first number from the range(i.e. 0) gets assigned to a. Hence the condition “a < 65536” is satisfied and control remains within the loop.

### Explanation
* We know that computer uses 2’s complement to represent data. For example if we have 1 byte (We can use char and use %d as format specifier to view it as decimal), we can represent -128 to 127. If we add 1 to 127 we will get -128. Thats because 127 is 01111111 in binary. And if we add 1 into 01111111 we will get 10000000. 10000000 is -128 in 2’s complement form.
Same will happen if we use unsigned integers. 255 is 11111111 when we add 1 to 11111111 we will get 100000000. But we are using only first 8 bits, so that’s 0. Hence we get 0 after adding 1 in 255.

* **MY: Because c++ doesn't wrong MAXIMUM NUMBER EXCEPTION**

## 7. C/C++ Preprocessors
* **#pragma Directive**: This directive is a special purpose directive and **is used to turn on or off some features**
* **#pragma startup** and **#pragma exit**: These directives helps us to specify the functions that are needed to run before program startup (before the control passes to main()) and just before program exit (just before the control returns from main()) SKIP

## 8. Operators in C / C++
* Bitwise Operators: ex: the bitwise AND represented as & operator in C or C++ takes two numbers as operands and does AND on every bit of two numbers. The result of AND is 1 only if both bits are 1.

        int a = 5, b = 9;   // a = 5(00000101), b = 9(00001001)
        cout << (a ^ b);   //  00001100
        cout <<(~a);       // 11111010

* ^ is Bitwise exclusive OR
* | is Bitwise inclusive OR
* <>= is Bitwise shift left/right assignment

## 9. Loops in C and C++
* Infinite loop

        for ( ; ; ) 
        { 
        printf("This loop will run forever.\n"); 
        } 

## 10. Decision Making in C / C++ (if , if..else, Nested if, if-else-if )
SKIM

## 11. Execute both if and else statements in C/C++ simultaneously
SKIP

## 12. How to compile 32-bit program on 64-bit gcc in C and C++
* To run in 32-bit computer: gcc -m32 geek.c -o geek

## 13. Switch Statement in C/C++
* SKIP

## 14. Functions in C++
* SKIM

## 15. Arrays in C/C++
* No Index Out of bound Checking: There is no index out of bounds checking in C/C++, for example, the following program compiles fine but may produce unexpected output when run.  
* **In C**, it is not a compiler error to initialize an array with more elements than the specified size. **For example, the below program compiles fine and shows just Warning.**
* **The program won’t compile in C++.** If we save the above program as a .cpp, the program generates compiler error “error: too many initializers for ‘int [2]'”

## 16. C++ string class and its applications
SKIM

## 17. Pointers in C and C++ | Set 1 (Introduction, Arithmetic and Array)

## 18. References in C++
* A pointer can be declared as void but a reference can never be void For example

        int a = 10;
        void* aa = &a; // it is valid
        void& ar = a;  // it is not valid

* The pointer variable has n-levels/multiple levels of indirection i.e. single-pointer, double-pointer, triple-pointer. Whereas, the reference variable has only one/single level of indirection. The following code reveals the mentioned points:  


        #include <iostream>
        using namespace std;
        
        int main() {
            int i = 10; // simple or ordinary variable.
            int *p = &i; // single pointer
            int **pt = &p; // double pointer
            int ***ptr = &pt; // triple pointer
            // All the above pointers differ in the value they store or point to.
            cout << "i = " << i << "\t" << "p = " << p << "\t"
                << "pt = " << pt << "\t" << "ptr = " << ptr << '\n';
            int a = 5; // simple or ordinary variable
            int &S = a;
            int &S0 = S;
            int &S1 = S0;
            cout << "a = " << a << "\t" << "S = " << S << "\t"
                << "S0 = " << S0 << "\t" << "S1 = " << S1 << '\n';
            // All the above references do not differ in their values
            // as they all refer to the same variable.
        }

* References are less powerful than pointers
* 1) Once a reference is created, it cannot be later made to reference another object; it cannot be reset. This is often done with pointers. 
* 2) References cannot be NULL. Pointers are often made NULL to indicate that they are not pointing to any valid thing. 
* 3) A reference must be initialized when declared. There is no such restriction with pointers.
* Due to the above limitations, references in C++ cannot be used for implementing data structures like Linked List, Tree, etc. In Java, references don’t have the above restrictions and can be used to implement all data structures. References being more powerful in Java is the main reason Java doesn’t need pointers.

## 19. Object Oriented Programming in C++
SKIP

# C vs. C++
SKIP

# C++ vs. Java

## 1. Comparison of Inheritance in C++ and Java
SKIM

## 2. Comparison of static keyword in C++ and Java
SKIM need more review