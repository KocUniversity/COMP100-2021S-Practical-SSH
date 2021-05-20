# VPN & LinuxPool Servers

In this practical, you will use Linux installed machines located at Koç University (KU) campus, namely Linuxpool servers. We allocate a server for you to work on, like a special cluster for you :) 

In order to be able to connect to these servers, you need a Virtual Private Network (VPN) client software. This is because servers are located in the KU network. VPN enables your computer to *pretend* that you are in the same network so that you can log in to the Linuxpool servers.

The first thing you need to do is setting up a VPN, which is going to be discussed in the next section.

## Setting up a VPN

KU IT has a website with instructions for [VPN access](https://confluence.ku.edu.tr/kuhelp/ithelp/it-services/network-and-wireless/vpn-access). Please follow the instructions for your operating system (OS). (See img/1.png)

Use your KUSIS ID and password here. For example, if your email is `username20@ku.edu.tr` then your KU NetID is "username20".  Ubuntu users (especially version 20.04) are recommended to follow "Open Source VPN client on Linux", which is relatively easier.

##  Connecting to a Linuxpool Remote Server via SSH (Secure Shell):

We've already covered `ssh` and `scp` in the lecture but we advise you to watch [this video](https://www.youtube.com/watch?v=rm6pewTcSro&ab_channel=Drupalize.Me) about the usage of 

* `ssh` to connect to a remote server,
* `scp` to transfer files between the remote server and your local machine.

You are going to use a terminal to connect to the Linuxpool server. We cannot do it on repl.it becase it's a cloud server located on another network (it's not possible to use the VPN client we intalled on our machine). 

Below, we explain different options for you, depending on your operating system. 

### Windows (via PowerShell)

The terminal software on Windows is called PowerShell. Open your terminal and type the following. (See img/2.png)

`ssh USER@linuxpool.ku.edu.tr`

Replace USER with your Koc University username. 

It will ask for your password, type your Koc University password. You’re good to go!

### Ubuntu / macOS

* Hit `CTRL + ALT + T` for Ubuntu. 
* Hit `CMD + SPACE` for macOS, then type Terminal. 

This will open a terminal window. Type:

`ssh USER@linuxpool.ku.edu.tr`

(Replace USER with your Koc University username).

Then, it will ask for your password, enter your Koc University password. You're good to go!


When you are finished with your work, you can disconnect by typing: 

`exit`

Your connection to the server may drop sometimes. In that case, you need to reconnect.
