# SrvPi
Setup project for RaspberryPi to act as a web server

## Steps to follow
* [01 - Os Install](OS_Install.md) - Raspbian installation on a "SD Card" from a Linux System
* [02 - Headless Basic Setup](Headless_BasicSetup.md) - Network configuration and SSH Access
* [03 - Basic Security Steps](Basic_Security_Steps.md) - Raspberry to act as a Web Server
* [04 - Client Access Setup](Client_Access_Setup.md) - Raspberry to act as a Web Server
* [05 - DHCPCD config](DHCPCD_config.md) - Raspberry to act as a Web Server


03 - ./Basic_Security_Steps (HOST_NAME=srvpi)

04 - ./Client_Access_Setup (USER_NAME=srv)

05 - ./DHCPCD_config


## APACHE  ##

06 - Linux/Apache_Install_General


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
