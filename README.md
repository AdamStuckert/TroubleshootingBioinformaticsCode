# Troubleshooting your bioinformatics code: N simple steps for new programmers, from someone experienced with failure.

## If at first you don't succeed...
Wait, you thought you would succeed the first time? This is science. That isn't how this works. That isn't how *any* of this works. Expect failure, and embrace it as part of your growth process. I've failed more times than I can possibly count.



Quick programming note (*ba-dum-tsss*): these are just things that I've found work well as a flow for me. List subject to grow at my whim. Feel free to send comments and baked goods as you see fit.

## General tips: 
1.	Did you actually type what you intended to? `ls` works a whole lot better to list the contents of a directory than `;s`, as I’ve repeatedly demonstrated.  

2.	 Do your files, data, etc exist where your program thinks you are looking? Trimmomatic doesn’t work if you don’t actually point the program to the directory where your data live.


## Scripting tips:
3.	A program you've called doesn't run at all. Does the program you are calling A) installed, B) live in your $PATH (in shell, for example), and C) is it executable?

...`which` name of program will tell you if the program has satisfied the above three conditions. If there is no output, ask whether you've installed it, added it to your path, and made it executable. If you haven't installed it, start there! Otherwise double check your $PATH, either by `echo $PATH`, or by viewing wherever you update your path (`.bashrc1`, `.bash_profile`, or `.profile`). If you've done both and the program still won't call, make sure you made it executable. Use `ls -lh` to check that you have executable privileges. If you do, there should be an `x` on the left hand side of the line. If not, make it so! `chmod u+x` ProgramName  

4.	Is it the right version of the program? `which` will also give you an idea about this. You might be calling python 3, whereas a program you are running requires python 2.  

5. *My for/while loop has been running for a long time and I don't know what is happening/can't see any output.*  Been there, done that. Two important things to note here. First, I think building a loop piecewise is good, and it is pretty critical to do it on a *small subset of your data/transcriptome/genome* instead of a 2.5 million line file. I'm a big fan of using `cat FILE | head > tmpFILE` to make a small, workable subset of the data to attempt a loop or any bit of code I'm writing. It is much better to waste 30 seconds running a subset, than 30 minutes running the whole thing and wondering. Second, following along with `tail -f OUTPUT` is a nice way to see things are actually happening, but only if you specify an output for each iteration. If you don't do that, you can add a line that tells you what iteration it is on (`echo $i` is a simple example).

6. The moment you think "I'm getting pretty good at Task X" is the moment that you accidentally create hundreds of nonsense files, make an infinite nested loop of files, or delete and entire hard drive (I won't mention any names). Bash and hubris don't mix, folks. Scratch folders are your friend.

## Not so much a troubleshooting mechanism, but rather a preventative one:

Don’t rely on your internet connection. Corollary: don’t expect that you won’t accidentally kill your command, or someone won’t do it for you. There are a variety of ways to do this, including but not limited to `nohup`, ctl/cmnd + z then `bg`, and `screen`. Personally, I like to use `screen -SL` and name my screen something informative (plzwork is also a plausible screen name, but generally a sign that I should quit for the day and come back to it with a fresh mind). `screen` is nice because I can detach from it, and then see the output in real time using `tail -f` and whatever the screenlog is. Further, it has the added benefit of being idiot proof, as well as generally life proof.   

See, for example:

![alt text](https://github.com/AdamStuckert/TroubleshootingBioinformaticsCode/blob/master/pics/IMG_20180314_181726396.jpg "oh no")

I love him, but sometimes he is an asshole. He is also the reason I gave in and started using Github: seeing 200 lines of code disappear is...disconcerting.

Still, look how cute he is.
![alt text](https://github.com/AdamStuckert/TroubleshootingBioinformaticsCode/blob/master/pics/IMG_20180118_075412379.jpg "ohmagawd he is so cute")

## Final notes

If you get stuck, ask for help! Very few people become proficient without the help of others, and this certainly includes me. People are generally helpful, *especially if you bribe them with food items and imbibements.*