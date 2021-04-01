C++ Basics (from the first lecture)
====================================

Moving from C to C++
--------------------

- C++ and C are (obviously) different. While you could write all your work in C and have no problem working with C++, you're losing out on a lot of good features of C++. Genuinely, don't do this.
- A majority of your issues when writing C++ can be solved by a web search (Google or otherwise). If you've ever taken a class in Java or Python, you'll know you can genuinely just type "how do I do X in Java/Python" and there will be 10+ results. 

Making a basic C++ file
------------------------

- A "basic" C file in your mind might look something like this:
    .. code-block:: C

        #include <stdio.h>
        int main(){
            int x = 1;
            printf("Printing #%d...\n", x);
            return 0;
        }
- A "basic" C++ file is basically the exact same. Since there are minor differences, here is the code:
    .. code-block:: C++

        #include <iostream>

        using namespace std; //will explain later
        int main(){
            int x = 1;
            cout << "Printing #" << x << "..." << endl;
            return 0;
        }

    - Obviously it's not that hard for you to search "how to print in C++", but just to save you a click, I added the above code.
    - You can see every new item that's printed is separated with "<<". Type is irrelevant.

Using Program Arguments
-----------------------

- If you've never used program arguments before, they're useful and they're not that bad. 
- Imagine this: 
    I made a random number guessing game, where I have six guesses to figure out which number was randomly chosen between 1 and 100. Cool, not a bad program.
    
    However, now my little brother comes in and wants to try it. He's really young, so maybe 1 to 100 is a bit much; I only want the program to run from 1 to 20 WITHOUT editing the code itself. How could we do that?

- A standard C++ main function could look one of two ways:
    - Without program arguments
        .. code:: C++

            int main(){
                //...
                return 0;
            }

        - No program arguments are taken
    - Or with program arguments
        .. code:: C++

            int main(int argc, char** argv){
                //...
                return 0;
            }
    
        - A variable number of program arguments are taken.
        - 'argc' represents the number of arguments
        - 'argv' is an array of c-strings (character arrays) representing each argument. 

- Here is an example, where each argument is printed on a new line:
    - printArgs.cpp:
        .. code:: C++

            #include <iostream>
            using namespace std;
            int main(int argc, char **argv){

                for(int x = 0; x < argc; x++){
                    cout << argv[x] << endl;
                }

                return 0;
            }

    - We compile the program:
        .. code:: bash

            g++ printArgs.cpp -o printMyArgs

    - Then run it:
        .. code:: bash

            ./printMyArgs
        
        Result:

        .. code:: bash
            
            ./printMyArgs

    - Then run it with an argument:
        .. code:: bash

            ./printMyArgs with_an_argument
        
        Result:
        
        .. code:: bash
            
            ./printMyArgs
            with_an_argument

    - Then run it with multiple arguments:
        .. code:: bash

            ./printMyArgs a b c d eeeeeee
        
        Result:

        .. code:: bash
            
            ./printMyArgs
            a
            b
            c
            d
            eeeeeee

- The first value in the c-string array (argv[0]) is always the name of the program. Every value following (argv[1], argv[2], ...) is an argument sent to the program from running it.

- The appeal of this is that, without taking user input in any way AND without changing any of the code, I just changed my output. Neato.