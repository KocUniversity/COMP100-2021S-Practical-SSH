# Remote Machines

We will use `ssh` to conenct to a remote machine, such as the KUACC cluster. The format is:

`ssh username@hostname`

or 

`ssh username@ipAddress`

For example, for our cluster, I use:

`ssh fguney@linuxpool.ku.edu.tr`

On the remote machine, we can display the (forwarded) remote shell and execute commands on the remote machine.

You can execute commands remotely. For example:

`ssh fguney@linuxpool.ku.edu.tr ls -la`

You can also pipe things. For example:

`ssh fguney@linuxpool.ku.edu.tr ls -la | grep start`

As you can see, I'm not entering my password everytime. If it was my first time connecting to the remote machine, it would ask for my password. In order to avoid entering the password, we can use *ssh keys* which is a public key encryption to create a pair of ssh keys: public key and private key. You give the server the public key, and whenever you try to connect to the server, it uses the private key to match the public key. So, you don't have to enter your password everytime.

You can create ssh keys by using `ssh-keygen` command. It will ask you where to store the key, typically ".ssh/id_rsa" folder in your home folder by default. Then it'll ask you for a password to encrypt the private part of the key. Without a password, someone can use your private key to impersonate you by using your private key, i.e. connect to the cluster as you.

You can check the keys by typing `ls -la ~/.ssh`, one for private and one for public. Check the content of the public key: `cat ~/.ssh/id_rsa.pub`.

In order to let the server know about this, we need to copy our public key there. We can do that by using `ssh-copy-id` command, it'll ask you for the password one last time.

`ssh-copy-id -i ~/.ssh/id_rsa.pub fguney@linuxpool.ku.edu.tr`

Now, we can ssh without typing the password from now on!

## Copying files to the remote machine

You can use `scp` command using this syntax:

`scp tmp.sh fguney@linuxpool.ku.edu.tr:tmp.sh`

`:` separates the remote mahcine's name and the path there. You can specify a different path on the machine or give it a different name, e.g. `:tmp2.sh`. 

Check if it is there:

`ssh fguney@linuxpool.ku.edu.tr ls`

`scp` will copy all the files even if some of them are already there. For copying a lot of files without recopying already copied stuff, a very useful command is `rsync`. It will match the content of two folders specified as input and copy only the changed files from the source to the destination, i.e. first to second in the argument list. 

`rsync -azP fguney@login.kuacc.ku.edu.tr:/kuacc/users/fguney/data/GCN/models/ /Users/fguney/tracking/data/GCN/models/`