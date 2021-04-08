How To Do Your Labs/Assignments
====================================

Making sure you're connected to the server
--------------------------------------------

- Making sure you're connected to the Unix server isn't too bad. 
    - If you're using purely SSH and Vim to get the coding done, you're an animal. And you probably don't need this guide.

    - If you're using purely SSH and copying the files from the server to your local machine (NOT using SSHFS in the guide I posted), then you don't necessarily need to be connected to the server when getting your work done. You just need to make sure you're connected when submitting. In that case make sure Putty/OpenSSH (or your standard SSH-in-terminal, if you're a Linux/MacOS user) are connected to the unix.ucsc.edu server. A way to test this is by running the following commands in your SSH client:
        .. code:: bash

            cd
            pwd

    If you see "/afs/cats.ucsc.edu/..." then you're connected :)

    - If you're using SSHFS, you still need an SSH client (Putty or OpenSSH). The benefit of SSHFS is not to completely remove SSH. It's just to minimize your usage of the command line. 
        - Windows: If you open your File Explorer to the "This PC" page (may show up on your left navigation bar), you should find a network drive. In my case, it was labeled ".", and it may be in yours too. If you see this drive at all, then you know you're connected to the server using SSHFS. 
        - Linux: SSHFS on Linux is short and sweet. Find your mount point (either in the graphical file explorer of your choosing or through the terminal), and enter that folder. If you see files, you're connected. If you don't, then you're not! Rerunning the SSHFS command *should* reconnect you. 
        - MacOS: Open Finder to the directory where you mounted the network drive. In my video, the location was my home directory (easy to identify in Finder as the place with the little house icon next to it). If you open it and find any files in it, then you're connected. 

Copying his code/PDFs/etc. for an assignment
-----------------------------------------------

- This one can seem a bit daunting if your Unix commandline experience is limited. Don't worry, I'll make it super clear (and if you're still confused, DM me on Discord: macmoholic#2221)

    - Open your SSH client (Putty, OpenSSH, terminal, etc.) to the unix.ucsc.edu server. 

    - Make a folder where you want to copy things over (this can be done using the command 'mkdir'. e.g, "mkdir Lab1" will make the folder Lab1).

    - Change directory into the folder "cd <foldername>"

    - Now, you want to use the copy command to bring the files from Professor Mackey's assignment folder into your new one. Go onto his website and find the "PWD" for an assignment/lab (should be in big, green text at the top). Then, run the command

        .. code:: bash

            cp -r <pwd>/* .

        (Make note of the "." at the end!!! You need that.)

    - The above command reads: "copy (cp), recursively (-r), everything in the folder (<pwd>/\*), to here (.)"

    - One final example:

    .. code:: bash

        mkdir Lab0
        cd Lab0
        cp -r /afs/cats.ucsc.edu/courses/cse112-wm/Assignments/lab0-intro-unix/* .

Get the work done on your end (using g++)
------------------------------------------

- Write code. Preferably using Visual Studio Code (it's pretty good). If you're a "FOSS" only person, mad respect: there is an open source, non-Microsoft version of VSCode.

- To test individual C++ files, you need to compile and run it. To compile using the GNU C Compiler (GCC), you can run:
    .. code:: bash

        g++ <filename>.cpp -o <executable>

        g++ main.cpp -o runnable_file

- Once your code is compiled into an executable file (in my example, called 'runnable_file'), you can run it! Just use:

    .. code:: bash

        ./<executable

        ./runnable_file

- **However**, you are NOT required to use g++ to compile and run all of the files in our projects! You can use 'make' to get a lot of your work done.
    - Once you're in the 'code' folder in the assignment, you can run:

        .. code:: bash

            make
    
    - And it should compile the program for you.

Make saves as you go
---------------------

- I believe you can use the submit command to make submissions as you go (like if you turned something in on canvas, but then made an edit and submitted the new one instead of the old one). But, I'm not 100% on that, so YMMV.

- You can make local saves, you can use git for version control, whatever works best for you. The main thing is: if you're writing code using SSHFS or SSH, the only way for you to lose your changes is if your connection with the server stops. This is unlikely, using SSH or SSHFS. Just... don't forget to do CTRL-S (or CMD-S if you're on a Mac) to save your work every so often :)

Submitting your assignment
----------------------------

- This also isn't too bad! Don't stress, and let me know if you're having issues.

- Make sure you're in your SSH client.

- The 'submit' command is really chill. You can run 'submit -m' to see the explanation on how it works. If you don't care, then keep reading.

- The format is "submit <class> <assignment name> <[files you want to submit]>". For example:
    .. code:: bash

        submit cse111-wm lab0 file1.cpp file2.cpp file3.cpp

- Seems easy, right? Just make sure your ssh client is in the correct folder, and this should literally be all you have to do.
