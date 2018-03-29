# Troubleshooting your bioinformatics code: N simple steps for new programmers, from someone experienced with failure.

## General tips: 
1.	Did you actually type what you intended to? `ls` works a whole lot better to list the contents of a directory than `;s`, as I’ve repeatedly demonstrated.  
2.	 Do your files, data, etc exist where your program thinks you are looking? Trimmomatic doesn’t work if you don’t actually point the program to the directory where your data live.


## Scripting tips:
3.	A program you've called doesn't run at all. Does the program you are calling A) installed, B) live in your $PATH (in shell, for example), and C) is it executable?

...`which` name of program will tell you if the program has satisfied the above three conditions. If there is no output, ask whether you've installed it, added it to your path, and made it executable. If you haven't installed it, start there! Otherwise double check your $PATH, either by `echo $PATH`, or by viewing wherever you update your path (`.bashrc1, `.bash_profile`, or `.profile`). If you've done both and the program still won't call, make sure you made it executable. Use `ls -lh` to check that you have executable privileges. If you do, there should be an `x` on the left hand side of the line. If not, make it so! `chmod u+x` ProgramName  

4.	Is it the right version of the program? `which` will also give you an idea about this. You might be calling python 3, whereas a program you are running requires python 2.  

## Not so much a troubleshooting mechanism, but rather a preventative one:

Don’t rely on your internet connection. Corollary: don’t expect that you won’t accidentally kill your command, or someone won’t do it for you. There are a variety of ways to do this, including but not limited to `nohup`, ctl/cmnd + z then `bg`, and `screen`. Personally, I like to use `screen -SL` and name my screen something informative (plzwork is also a plausible screen name, but generally a sign that I should quit for the day and come back to it with a fresh mind). `screen` is nice because I can detach from it, and then see the output in real time using `tail -f` and whatever the screenlog is. Further, it has the added benefit of being idiot proof, as well as generally life proof.   

See, for example:

![alt text](https://drive.google.com/open?id=0BwmkczhV3LaHaTVQNzB0WUJoSDZod09jem1PVTktbU9LQnBJ "oh no")

I love him, but sometimes he is an asshole. He is also the reason I gave in and started using Github: seeing 200 lines of code disappear is...disconcerting.

Still, look how cute he is.
![alt text](https://drive.google.com/open?id=0BwmkczhV3LaHaE9aZ1ItRExMa2UwcnltQ2tacW04akJuWU5r "ohmagawd he is so cute")

