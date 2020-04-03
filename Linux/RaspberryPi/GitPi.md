Steps to follow:
01 - ./OS_Install

02 - ./Headless_BasicSetup

03 - ./Basic_Security_Steps (HOST_NAME=gitpi)

04 - ./Client_Access_Setup (USER_NAME=git)

05 - ./DHCPCD_config


## GIT ##

06 - Git :
      Install Git:
        sudo apt-get install git

07 - Login as git user to Gitpi server, and create repository:
      New project:
        git init --bare project.git

      Existing project:
        git clone --bare project project.git

      This step is to make sure the owner of the repository is user 'git'

08 - Login as 'pi' (sudoer) user to Gitpi server, and mv previously created
     repository to /srv/git:
      If not already created /srv/git:
        sudo mkdir /srv/git

      Move Repository:
        sudo mv /home/git/project.git /srv/git
