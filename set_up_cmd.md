# TERMINAL SET UP

**Palmetto Cluster Access**

A supercomputer can be accessed and used from your personal computer via the terminal, also called a command line interface (CLI). Different operating systems have different CLIs. But the interfaces look relatively the same. Request a connection to the super computer by using the command `ssh`:
```sh
  ssh <username>@slogin.palmetto.clemson.edu
```

## Linux/Unix basic commands

```sh
    # change current working directory to its immediate parent directory
    cd ..
    
    # copy document to different directory
    cp my_document.pdf /home/user/documents/

    # copy file to different directory and rename it
    cp /path/to/original/file.txt /path/to/destination/new_file_name.txt

    # rename a file or directory
    mv old_filename new_filename
    mv old_directory_name new_directory_name 

    # create new folder
    mkdir directory_name

    # view contents of a file in the terminal
    cat filename

    # edit and/or create a file
    nano filename

```

## .bashrc

The `.bashrc` is a user-specific shell script that is read and run on non-login nodes (ie. interactive nodes). This is an ideal place to configure personal commands that you want to apply to every new terminal window you open. This file will be located in your `/home/` directory. It is a hidden file, denoted by the `.` in `.bashrc`. 
```sh
# change directory to home, shortcut: ~
cd ~
# edit .bashrc file using a text editor, nano
nano .bashrc
```
There will be text already in the `.bashrc` file. It can be useful to add 1) custom paths to scripts 2) aliases, or custom shortcuts or 3) custom prompt formatting
```sh
### edit text inside .bashrc file
### this is what is in mine (all optional)
# color styles
# export PS1='\[\033[0;32m\]\u@\h\[\033[00m\]:\[\033[0;37m\]\w\[\033[00m\]\$ '
export PS1='\[$(tput setaf 15)\](\[$(tput setaf 70)\]\u\[$(tput setaf 15)\]@\[$(tput setaf 214)\]\h\[$(tput setaf 15)\])-[ \[$(tput setaf 38)\]\w\[$(tput setaf 15)\]]\[$(tput sgr0)\]$ '

## aliases

# environment and packages shorthand
alias conda3='module load anaconda3/2023.09-0'
alias assembly='source activate asm_env'
alias r_stat='module load r/4.3.0'

# shorthand for navigation
alias nero='cd /project/viper/venom/Taryn/Nerodia/'

# misc batch job and interactive job
alias interactive='salloc --nodes=1 --ntasks-per-node=1 --cpus-per-task=16 --mem=48G --time=12:00:00'
alias save_scratch='find /scratch/tecorn -used tecorn -exec touch {} +'
alias check='squeue -u tecorn'
```
Documentation: https://www.digitalocean.com/community/tutorials/bashrc-file-in-linux

Resource for altering bash prompt: https://robotmoon.com/bash-prompt-generator/ https://bash-prompt-generator.org/ 

## Anaconda

```sh
 # load anaconda into terminal
 module load anaconda3/2023.09
```

**Navigating Anaconda**

```sh
 # list your environments
 conda env list

 # remove an environment
 conda env remove -n env_name
```

**Create Environments and load packages**
```sh
 # load module anaconda in an interactive job
 module load anaconda3/2023.09
 # create environment (ex. assembly environmnet) to save packages (hifiasm)
 # the addition of mamba loads mamba while creating the environment
 conda create -n hifiasm mamba
 conda activate hifiasm
 mamba install -c bioconda hifiasm
```

```sh
 module load anaconda3/2023.09
 # create enviornment for BBMap (includes bbstats, samtools)
 conda create -n bbmap mamba
 conda activate bbmap
 mamba install -c bioconda bbmap
```

```sh
conda create -n edta mamba
conda activate edta
mamba install -c conda-forge -c bioconda edta
``
---
## Apptainer
```sh
apptainer pull funannotate_latest.sif docker://nextgenusfs/funannotate:latest

# linked to my apptainer environment all the tools in bin:
apptainer exec --bind /project/viper/venom/John_Henry/bin:/opt/tools funannotate_latest.sif bash
```
