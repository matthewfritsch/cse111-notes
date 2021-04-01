C++ types/features/etc. that are not in C
=========================================
String
------
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

Vector
------

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


Auto
----

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

Classes
-------
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

Namespaces
----------
- In C++, namespaces exist for preventing name conflicts/confusion in large projects. We will most likely use namespace std (standard) most of the time.
- Example without "using namespace std", but with using features from the std namespace:
    .. code:: C++

        #include <iostream>

        int main(){
            std::string str = "hello";
            std::cout << str << std::endl;
            return 0;
        }
    
- Example with "using namespace std":
    .. code:: C++

        #include <iostream>
        using namespace std;

        int main(){
            string str = "hello";
            cout << str << endl;

            return 0;
        }

- If you've used C++ before, you will probably know that the std namespace is really, really common. You're unlikely to use other namespaces (unless Professor Mackey provides one!)
    
Static Casting
--------------

- Casting is a way of changing the type of a variable to a different type. In C, sometimes this was as easy as

    .. code:: C

        float f = 3.14;
        int i = f; //this
        int j = (int) f; //or this

- While this is technically still available in C++, casting is now sketchy. If you cast one object variable to another type, it's possible you'll run into runtime errors. Yikes.
- **Static Casting**: In the first lecture, Professor Mackey really only discussed using static casting, so that's all I'm going over right now:

    .. code:: C++

        float f = 3.14;
        int i = static_cast<int>(f);

        char c = 'x';

        //this is bad, and might produce runtime errors:
        int* badptr_to_c = (int*) &c;
        //do this instead!
        int* ptr_to_c = static_cast<int*>(&c);

