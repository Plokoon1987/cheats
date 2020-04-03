Ref: https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server

USER_NAME: Username chosen to access the server

Creating a user to centralize all developers in server:

In Terminal:
  Creating user:
    sudo adduser USER_NAME

  Creating ssh structure:
    su USER_NAME
    cd
    mkdir .ssh && chmod 700 .ssh
    touch .ssh/authorized_keys && chmod 600 .ssh/authorized_keys


To add access to server user either:
  On developers' terminal, copy id.pub using:
    ssh-copy-id USER_NAME@192.168.1.35 (To copy id.pub to host)

If you don't want to give them the password, ask them for their public id:
  In terminal:
    cat /tmp/id_rsa.john.pub >> ~/.ssh/authorized_keys
    cat /tmp/id_rsa.josie.pub >> ~/.ssh/authorized_keys
    cat /tmp/id_rsa.jessica.pub >> ~/.ssh/authorized_keys

