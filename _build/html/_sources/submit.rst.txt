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

Get the work done on your end
------------------------------

Make saves as you go
---------------------

Submitting your assignment
----------------------------

