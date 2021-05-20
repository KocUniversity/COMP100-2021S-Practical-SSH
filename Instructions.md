# SSH to a Remote Machine

For this part, please first, refer to LinuxPooL_VPN.md file to setup your environment so that you can connect to the Linuxpool server.

1. As you can see, you have to enter your password every time you ssh to the server. This becomes annoying after a while. For the server to remember us, we can generate a pair of keys on our local machine by using `ssh-keygen` command. Follow the steps, by choosing a directory and a passphrase as prompted. Then check the directory to see the key pair created. 

Now, we need to copy the public key, i.e. the one that ends with .pub, to the server. We do that by using the `ssh-copy-id` command:

`ssh-copy-id -i ~/.ssh/id_rsa.pub USER@linuxpool.ku.edu.tr`

Enter your password one last time and done! Check if it works by doing multiple logins without needing your password.

**Note:** If you're on Windows, `ssh-keygen` part is the same but `ssh-copy-id` is not available. So you need to copy your key "by hand" by doing the following:

`cat env:USER\.ssh\id_rsa.pub | ssh USER@linuxpool.ku.edu.tr 'cat >> ~/.ssh/authorized_keys'`

`env:USERPROFILE\.ssh\id_rsa.pub` is the location of your public key, e.g. `C:\Users\cagan/.ssh/id_rsa.pub` for your TA. If you get confused, please refer to powershell.png under the img folder.

2. Let's dive a bit deeper into the rabbit hole. Linuxpool server actually consists of multiple servers, 6 to be precise, to be able to accommodate all of you. You might have noticed that you are redirected to a different one each time you login, linux02 or linux05, etc. 

For some reason, as you will see in the next part with screen and tmux, you need to be able to switch between servers. While we are logged into one of them, we can ssh to any of them. Let's say we are on linux05, and we want to switch to linux01. All we need to do is:

`ssh linux01`

Why didn't we need the username? Why not `ssh USER@linux01`?

The problem is linux01 does not recognize us coming from linux05. In other words, it does not have a key matching mechanism like the one we created in step 1 between our local machine and the Linuxpool server. As you might guess, we need to the same here on the Linuxpool to be able to jump between servers easily without needing to enter our pasword every time. Use `ssh-keygen`, and then `ssh-copy-id` as we did in the first step.

By doing this for only one of them, we are able to ssh to any of them without a password. We didn't need to repeat it for all the 6 linux servers. Any wild guesses, why?

**Hint1:** Remember what happens when we do `ssh-copy-id`. If we only need to do it once, and then all the servers can see it, what does it mean? 

**Hint2:** Do `pwd` on different servers, and explain what you see.

