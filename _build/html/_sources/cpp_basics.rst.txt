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

C++ types that are not in C
----------------------------
- string
    - "What? Strings exist in C, what the heck". Yeah, but now they're basically Java strings(except they're NOT OBJECTS. Java, you suck.)

        .. code-block:: C++

            #include <string>
            #include <iostream>

            using namespace std;
            int main(){
                
                string s = "a string!";
                
                char c = s[3];
                cout << c << endl;
                cout << s[2] << endl;
                cout << s << endl;
                cout << s.substr(2, 6) << endl;
                //choose the next 6 letters starting at index 2. Should print out "string"

                s = "a new string!";
                s = "one more string, with a newline??\n";

                return 0;
            }

    - strings are totally usable with or without the string header (though if you're using strings, might be worth including it.)
    - There are TONS of functions associated with the string type. It's worth looking into if you really care. 
    - You may also notice that there is no null terminator OR deletion of data associated with the strings. They're all made on the stack, so do whatever you want you maniac.
- vector
    - If you've used ArrayList<> in Java, this is that. You can skip this block.
    - A vector is a variable-length array (aka, a list) of a type. Think LinkedList, but you didn't have to make it or any of the functions associated with it.
        .. code-block:: C++

            #include <iostream>
            #include <vector>

            using namespace std;
            int main(){
                vector<int> v; //an empty vector that holds ints

                v.push_back(1); //it now holds 1.

                cout << v.at(0) << endl; //prints out 1
                cout << v[0] << endl; //prints out 1

                v.clear(); //the vector is empty now.

                vector<int> w{8,6,7,5,3,0,9}; //a vector with values 8, 6, 7...
                //I want to delete the 7 at index 2. I can use v.erase, but I CANNOT use v.erase(2)

                vector<int>::iterator i = v.begin();
                v.erase(i+2); //this works. Yuck.
                //can also do v.erase(v.begin()+2)
                
                //insert at index 2 the number 4
                v.insert(i+2, 4);

                return 0;
            }


- auto
    - auto is actually badass. I doubt you need to use it all the time, but you probably could.
    - You can define variables without knowing their types:
        .. code-block:: C++

            //...
            int x = 0; //this is an int. duh.
            auto a = 0; //this is also an int
            auto b = x; //int
            auto* b = &x; //pointer to an int
            //you get the picture...

    - You also don't need to type a bunch to get the correct type written out:
        .. code-block:: C++

            //...
            vector<string> allNames;
            //...
            //now we want to iterate through the vector in a for loop

            //we could write this
            for(vector<string>::iterator i = v.begin(); i != v.end(); i++){
                //something is going on in this for loop
            }

            //or, we could write this
            for(auto i = v.begin(); i != v.end(); i++){
                //something is going on in this for loop
            }
            //textually it doesn't look like a big difference. But do you really want to type "vector<string>::iterator" instead of "auto"?

- Classes
    - Now you can make actual classes in separate files (or in the same, if you like anarchy)
        - main.cpp
            .. code-block:: C++
                
                #include "Person.hpp"
                int main(){

                    Person p("Sammy", 22);
                    p.setStudent(true);
                    
                    return 0;
                }

        - Person.hpp
            .. code-block:: C++

                #IFNDEF PERSON_HPP_
                #DEFINE PERSON_HPP_

                #include <string>
                using namespace std;

                class Person{
                    private:
                        string name;
                        int age;
                        bool isStudent;
                    public:
                        Person(string, int);
                        Person();
                        ~Person();
                        void setStudent(bool);
                }

        - Person.cpp
            .. code-block:: C++

                #include "Person.hpp"

                Person::Person(){ //default constructor
                    name = "";
                    age = 0;
                    isStudent = false;
                }
                Person::Person(string newName, int newAge){ //nondefault constructor
                    name = newName;
                    age = newAge;
                }
                Person::~Person(){ //destructor
                    name = "";
                    age = 0;
                    isStudent = false;
                }

                void Person::setStudent(bool studentVal){ //mutator
                    isStudent = studentVal;
                }
