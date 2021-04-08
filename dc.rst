What is dc, and how do I use it?
==================================

What is dc?
------------

- 'dc' is an arbitrary precision, reverse-polish calculator. The name 'dc' is short for 'desk calculator'.
- Its purpose is, obviously, to be a basic calculator. Though, this calculator doesn't behave exactly like a TI-84 or an iPhone calculator. dc is written to have no upper limit.
- If you wrote a simple calculator in C++ right now (entering in digits and operators using cin), then you would find an upper limit pretty quickly (try doing 2,000,000,000 * 2,000,000,000 * 2,000,000,000).
- The purpose of dc is to have arbitrary precision, meaning it will run out of digits only when your system runs out of memory to create more digits. 
- When using the program, numbers are added to a stack. Operations are performed on members of the stack.
  

How do I use it?
----------------

- In any Unix system with dc installed, run dc:
    .. code:: bash

        dc

- You can't use the standard equation format you're most likely used to (e.g "5*4"). You need to add values to the stack, and then provide an operation:
    .. code:: bash

        5 4 //this is where I added both values to the stack. You can put plenty of numbers here
        f //this is to print out the stack. The next two lines should both be numbers, since I only have two digits in the stack.
        4 //the program prints out 4 since it was last added to the stack
        5 //the program prints out 5 since it was added to the stack before the 4
        c //'c' is used to clear the stack.
        f //nothing is printed because the stack was cleared.

- Here is a sort of glossary of commands/operations you can use (these can also be found in the manpage of dc)
    - Quit Command
        - **q:** quits the program
    - Printing Commands
        - **p:** print the top value of the stack, without changing the stack.
        - **n:** print the top value of the stack, and pop it off. Does NOT print a newline.
        - **f:** print the full contents of the stack, without changing the stack.
    - Arithmetic
        - **+:** pop the top two values from the stack, add them, and push the result.
        - **-:** pop the top two values from the stack, subtract them (bottom minus top), and push the result
        - **\*:** pop the top two values from the stack, multiply them, and push the result.
        - **/:** pop the top two values from the stack, divide them (bottom divided by top), and push the result
        - **%:** pop the top two values from the stack, find the remainder of their division (bottom modulus top), and push the result
        - **~:** pop the top two values from the stack, divide them (bottom divided by top), and push the result as well as the remainder
        - **^:** pop the top two values from the stack, exponentiate (bottom to the power of top), and push the result
        - **v:** pop the top value, compute the square root, and push the result
    - Stack Control
        - **c:** clear all values from the stack
        - **d:** duplicate the top value of the stack, and push it to the stack.
        - **r:** reverse all values of the stack
        - **R:** take the top value off of the stack (call it n). select the top n values of the stack, and cyclically rotate them (e.g 3 2 1 0 would make n = 3. The top three values of the stack [2, 1, 0] are rotated once [0, 2, 1])
    - There are more, but I'm leaving out Registers, Parameters, and Strings because I don't think those are super pertinent to our experience with dc. If they are, I will add these later.
        
        

        