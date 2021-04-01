Working with the Unix Timeshare
===============================

What is the Unix Timeshare
--------------------------
- The UCSC Unix Timeshare is a server that every student is allowed to connect to. The purpose of the server is to provide a place for storing student files, as well as for distributing an environment with the same software for every student.
- For example, your personal computer running Windows/MacOS etc. may not have a C++ compiler installed on it. But if you connect to the Unix Timeshare, you (and every other student) have the means to compile and run C++ code.

How to get on the Timeshare using SSH
-------------------------------------
- The Unix Timeshare can be accessed from the its.ucsc.edu website here: (https://its.ucsc.edu/unix-timeshare/tutorials/how-to-connect.html)
- SSH, as described in the above link, is a terminal/console only program that connects a user (you) to an SSH host (the server).
- Some Linux Commands include:
    - 'ls': list all files in the current directory
    - 'pwd': print the current directory (your location in the system)
    - 'mkdir': make a directory provided a name. e.g 'mkdir stuff' would make a directory called stuff.
    - 'rmdir': the same as mkdir, but removes a directory. Only removes if it's empty.
    - 'touch': same as mkdir, but for non-folder files. 'touch prog.py' would make a file called prog.py
    - 'rm': same as rmdir, but works on non-folder files. 
        - 'rm -r': this will recursively remove items from a directory. If you have a folder called 'MyFolder' with 100 items in it, using 'rm -r MyFolder' will remove ALL the items in the folder. 
        - **To be really clear**, this does NOT move items to a recycle bin that you can bring back. These files are gone forever, so be really careful with this.
        
A better way to get on the Timeshare
------------------------------------
    - For those who are not super into working with the command-line and MUCH prefer working with their Windows File Explorer/MacOS Finder, you will likely want an alternative.
    - Introducing SSHFS: Using SSH to create a temporary file system on your computer that, as you edit, is updated on the Unix Timeshare.
    - Here are a couple videos I made on how to get SSHFS to work on your system:
        - Windows:
            .. raw:: html

                <div style="width:100%;height:0px;position:relative;padding-bottom:56.250%;"><iframe src="https://streamable.com/e/anz77q?loop=0" frameborder="0" width="100%" height="100%" allowfullscreen style="width:100%;height:100%;position:absolute;left:0px;top:0px;overflow:hidden;"></iframe></div>

        - Linux:
            .. raw:: html

                <div style="width:100%;height:0px;position:relative;padding-bottom:56.250%;"><iframe src="https://streamable.com/e/1d6q99?loop=0" frameborder="0" width="100%" height="100%" allowfullscreen style="width:100%;height:100%;position:absolute;left:0px;top:0px;overflow:hidden;"></iframe></div>
            
            - codeconnect.sh:
                .. code:: bash
                    
                    sudo mkdir ~/UCSC_UNIX
                    cd ~
                    sudo chown matthew UCSC_UNIX
                    chmod 777 UCSC_UNIX
                    sshfs <yourCruzID>@unix.ucsc.edu:/afs/cats.ucsc.edu/users/p/<yourCruzID> ./UCSC_UNIX

        - MacOS:
            .. raw:: html

                <div style="width:100%;height:0px;position:relative;padding-bottom:56.250%;"><iframe src="https://streamable.com/e/zfyo14?loop=0" frameborder="0" width="100%" height="100%" allowfullscreen style="width:100%;height:100%;position:absolute;left:0px;top:0px;overflow:hidden;"></iframe></div>

            - sshfs command:
                .. code:: bash
                
                    sshfs <yourCruzID>@unix.ucsc.edu:/afs/cats.ucsc.edu/users/p/<yourCruzID> ./UCSC_UNIX
