1.)about the env
##Background
I reinstall my OS to ubuntu. This time, the gnuradio has updated to 3.7.9. I still tried the original installation through compiling source code, but I failed, because I could not path the "make test".

##Problem:
I turn to pybomb. Everthing goes fine. But when compiling my original modules, I find something wrong. Sorry, I forgot to copy the error. But the bried idea is " the compiling is incomplete".
Note that, this module has proved to be all corrected and finely installed in previous system. 

##Analysis:
I gauss the reason is about the environment. Because in the previous system, I installed through compiling, so the environment has been setup, PATH, PYTHONPATH, etc have been set. But pybombs installed so clean that we have not change anything. That's why everytime we open a new terminal, we have to "source setup_env.sh"

##Solution:
I need to make the environment variables changed permenently. 
###Steps:
1. I copy the four line "export PATH=xxxxxxxx" in setup_env.sh to the end of file of "~/.profile"
2. Logout and login   or  restart
3. done!

2) Pybomb install OOT
Because the install directory of pybomb is not the same with those who installed by compiling, so we should replace
```
cmake ../
```
with
```
$ cmake -DCMAKE_INSTALL_PREFIX=<target_directory> ../ # <target_directory> should be the configured PyBOMBS target
```
something like
```
$ cmake -DCMAKE_INSTALL_PREFIX='/home/user1/gnuradio/target' ../
```