# Linux-helper_rep

Created from "Eli the computer guy" youtube channel

***** SUDO *****
Use sudo to act as administrator (windows), to install things or to make modifications.


***** MAN PAGES *****
These pages include descriptions of the programs used in LINUX, ie:

	- man apt-get: will show a description of the programs, commands and arguments to be used
	with apt-get

	- man ping: same as above..., but explaing ping

To exit press "q"

***** TASKSEL *****
Tasksel stands for "task Select", it is used to install the different packages to run certain things,
ie: LAMP, e-mail server, NAS server
run: "sudo tasksel"

 
***** APT-GET *****
The "apt-get" program is used to install programs. It gets the programs from repositories instead of
CDs.

To run use "sudo"

ie: sudo apt-get install apache2
    sudo apt-get remove apache2
    suda apt-get upgrade

***** SERVICES *****
Example using apache2
sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 restart


***** TOP *****
Top is the taskmanager of linux. It assigns a process Id to the processes (PID)

To run use: - sudo top
To kill a process press "k" while running Top and the PID of the process to be killed 


***** CD *****
CD stands for "change directory"

ie:
	- cd work 	#to enter folder work in current directory
	- cd /work	#to enter folder work in root directory

Capitalization matters in Linux (filenames or folders)

	- cd ~ 		#takes us to home folder
	- cd /		#takes us to root folder

To list files in folder use "ls"
To lista All files in directory use "ls -la"