Lab Report 1
=========

## Tutorial on Remote Access

__Step 1: Installing VSCode__

Go to [this link](https://code.visualstudio.com/) and download and install VSCode onto your computer. When it is installed, open the application and you should have a window that looks like this:

![Image](https://imgur.com/a/kId7l7j)


__Step 2: Remotely Connecting__

Open a terminal in VSCode and type in 

```
ssh cs15lwi22amj@ieng6.ucsd.edu
```

If it is the first time you've connected to this server, it will ask you to confirm your connection. Answer yes to this prompt, type in your UCSD password, and the following screen should appear:

![Image](https://imgur.com/a/1Crza8X)


__Step 3: Trying Some Commands__

We can now run commands on the remote server. Feel free to test out terminal commands. For example:

![Image](https://imgur.com/a/MK9jrL3)

Here, the command "cd" changes the current directory. I changed the current directory to "perl5".


__Step 4: Moving Files with scp__

First, logout of the remote server with the command `logout`. Find the name of the file you want to move to the remote server. For this I will use `WhereAmI.java` as an example.

Then, run the command

```
scp WhereAmI.java cs15lwi22amj@ieng6.ucsd.edu:~/
```

Enter your UCSD password again. Then type in `ssh cs15lwi22amj@ieng6.ucsd.edu` to log in the remote server. Type `ls` to list all the files in the server and your file should appear in that list.

The following image demonstrates these steps:

![Image](https://imgur.com/a/m1y6Vug)


__Step 5: Setting an SSH Key__

Make sure that you are on your computer directory and not the remote server. Then type `ssh-keygen`. The file in which to save the key should be the path given in the parentheses. The passphrase should be empty. The following image shows this process:

![Image](https://imgur.com/a/EeIKRyR)

Then, using the following code block, copy the public key to the `.ssh` directory to the remote server.

```
$ ssh cs15lwi22zz@ieng6.ucsd.edu
<Enter Password>
# now on server
$ mkdir .ssh
$ <logout>
# back on client
$ scp /Users/lmei2021/.ssh/id_rsa.pub cs15lwi22amj@ieng6.ucsd.edu:~/.ssh/authorized_keys
# You use your username and the path you saw in the command above
```

Then you can now `ssh` or `scp` without prompting your password:


![Image](https://imgur.com/a/ib3whJI)


__Step 6: Optimizing Remote Running__

We can now optimize the process for making a local edit to a file, then copying it to remote server and running it.

Using `WhereAmI.java` as an example, we can utilize the commands 

```
scp WhereAmI.java cs15lwi22amj@ieng6.ucsd.edu
ssh cs15lwi22amj@ieng6.ucsd.edu "javac WhereAmI.java; java WhereAmI"
```
The first command copies the file into the remote server. The second command logs in to the remote server, then runs `javac WhereAmI.java; java WhereAmI` in the remote server, then immediately logs out of the remote server after executing these commands.

We first type these commands into VSCode manually when it is our first time going through this process. Then, we can use the up arrow to access these commands that we have written to make the process quicker.


![Image](https://imgur.com/a/Xu3zey3)


I first edited the `WhereAmI.java` file, then I used the up arrow key to access these two commands and ran them. I got this process to be consistently under 5 seconds.




