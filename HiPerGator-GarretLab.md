# HiPerGator: User Manual [GarrettLab](https://www.garrettlab.com/)
                                                             by Ricardo I. Alcalá 
                                                               -- ralcala@ufl.edu

## Connecting to HiPerGator computer
First thing you need is an `ssh client`, which is the secure shell protocol to connect through the internet to HiPerGator  (**HPG**) ``ssh server`` .
 
 **If you own:**
- a unix system ``Mac or Linux`` just open the **terminal**.
- a pc computer with ``Windows`` just download [cygwin](https://www.cygwin.com/) or [mobaxterm](https://mobaxterm.mobatek.net/) and install it, etc... 

#### Connecting with ssh:
To connect to HPG using your `ssh client` type
```bash	
ssh gatorlink@hpg.rc.ufl.edu
```
type your **UF password**.
<sup>Tip:  you can also login to `hpg1` and `hpg2` if specified at login.<sup>

<small>**Notes:** the command line is the way to communicate with the **HPG** cluster computer. However, keep in mind, that with the **HPG** there are a couple of steps before start working on it. First, remember that the hipergator is a supercomputer or a computer cluster, which also means that there is a 'central' node that controls the rest of the nodes in the **HPG**.  Therefore, when you login, you logged in to the _main node_, therefore, is recommended to avoid executing tasks in there. For that reason, there is a `developmental session` to run singles tasks or use the SLURM scheduler using a sbatch script.<small>

--------------------------------------------
Now that you are connected to **HPG** with **Red Hat** as _Operative System_ (OS), one of the many flavors of Linux,  regular ``bash`` command language can be used once logged in. 
```bash
#bash commands
pwd		  # print working directory
cd 		  # change directory
ls 		  # list files
mv		  # move files
cp		  # copy files
mkdir     # make directory
rm 		  # remove files ## be carefully, once deleted no regerts
more	    # display files
cat		  # read & concatenate files
nano	    # create a text file
```  

------------------------------
## HiPerGator Session
**First step**
 - LOADING MODULES
This unix/linux version require to load the modules (or software),  
using the following sintax ``module load``, if you want to display all software @HPG type `module spider` to check the whole list of software  <small>**note:  press `q` to exit.** <small>
 ```bash
 # loading modules, example with R
 module load R 
 R
 #'@ This command will initialize R 
 R version 3.6.3 (2020-02-29) -- "Holding the Windsock"
Copyright (C) 2020 The R Foundation for Statistical Computing
Platform: x86_64-pc-linux-gnu (64-bit)
R is free software ...
....
 ```
<small>**Note: Remember that working like this you are executing on the _main node_, and if wrong doing, they can get your account suspended** <small>

 - DEVELOPMENT SESSION
Running the development sessions allow you to request resources from the HPG, one node with _N_ gigabytes of RAM, or _x_ number of nodes and tasks for _t_ time, therefore if you want to request a node to try your code, load the `ufrc` module and type:
```bash
# loading the ufrc module and invoking the development session
module load ufrc      
srundev --mem=8gb --ntasks=1 --cpus-per-task=1 --time=04:00:00
# or symply allocate standard resources specifying the time only  
srundev -t 160  
```
 - EXECUTING SBATCH SCRIPTS
 ```bash
#@ HAVE NOT GET THERE YET 
 ```

 
 ### Moving files from HPG to your computer 
Secure file transfer protocol or **SFTP** is a network protocol that allow you to transfer files from your computer to the HPG, instead you can use an SFTP client such as [FileZilla](https://filezilla-project.org/) or [Cyberduck](https://cyberduck.io/).
Open your terminal and connect to HPG typing the following command:
```bash
# sftp
sftp gatorlink@sftp.rc.ufl.edu
put name_of_your_local_file
get name_of_your_remote_file
```


------
**HPG to local**
`scp gatorlink@hpg.rc.ufl.edu:/home//PATH_TO_FILE .`

**local to HPG** 
`scp myfile gatorlink@hpg.rc.ufl.edu:/home/gatorlinkralcala/PATH_TO_FILE`

### SFTP protocols from hypergator
`module load ncftp`
`ncftpget -R ftp://ADDRESS`

------
#### Useful commands
**job queue**

```
squeue -u gatorlink
```
```
squeue --qos epi <or> plantpath
```

**Association**
```
showAssoc username
```

**quota**
```
lfs quota -g garrett /ufrc
```
