opentree vagrant
################
This repo has the input files needed to bootstrap a vagrant ( http://www.vagrantup.com/ ) virtual
machine with the opentree of life software tools

Installation
############
After installing vagrant, 

    $ cp set-up-web2py-user.mysql.txt.Example set-up-web2py-user.mysql.txt

Then edit set-up-web2py-user.mysql.txt if you want to change the db passwords used by the web apps

The commands for booting the virtual machine and logging in are:

    $ vagrant up
    $ vagrant ssh

Launching software
##################

To launch phylografter:

    $ cd $OPEN_TREE/web2py
    $ echo 'your preferred web2py admin password here' | python web2py.py --nogui -i 192.168.33.10 & 

or:

    $ python web2py.py --nogui -a '<recycle>' -i 192.168.33.10 & 

if you have previously launched web2py and entered an admin password. 192.168.33.10 is the
IP listed in the Vagrantfile as the virtual machine's IP. After doing this, you should be able to see
open tree software at http://192.168.33.10:8000/phylografter and  http://192.168.33.10:8000/opentree

If you need to have access to the admin section of web2py, launch it without the -i and IP address.
This will cause web2py to bind to the loopback (localhost, or 127.0.0.1) address. Then you can
 log out of the virtual machine and use:

    $ vagrant ssh -- -L 8000:127.0.0.1:8000

to establish an ssh tunnel from port 8000 on the host machine to port 8000 on the virtual machine.
This should give you open tree services at http://127.0.0.1:8000/phylografter http://127.0.0.1:8000/opentree