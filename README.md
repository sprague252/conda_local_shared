# conda_user_shared

Scripts and configuration files to move user conda environments and configuration files to a shared drive.

**Note**: These scripts and files are optimized for the student laptop and desktop Macintosh computers in the East Carolina University (ECU) Department of Physics, but they can be configured to work on any POSIX computer.

## Overview

This package contins a BASH configuration script `conda_user_setup` that replaces the `~/.conda` directory and the `~/.condarc` user configuration file with symlinks to another directory.  If that other directory is on a shared drive, such as the ECU Pirate Drive, that is mounted on any of the student computers, the user only has to run a minimal installation script contained on the shared drive in order to access user-installed Conda configuration files and environments.  This eliminates the need to re-install environments each time the user logs onto a different computer.

## Files

* `conda_user_setup` - BASH script that configures the computer to use the shared drive by replacing the `~/.conda` directory and the  `~/.condarc` user configuration file with symlinks to the shared drive.  The script also has the option to run `conda init`, which configures the user's `.bash_profile` file to add the appropriate conda environment variables on shell startup.

* `conda` - Directory to hold the user's conda environment files on the shared drive.  The user's `~/.conda` directory is replaced with a symlink to this directory.

* `LICENSE` - copy of the *GNU General Public License v3.0*, under which this package is distributed.

* `README.md` - This file.

## Installation

### Brief instructions for the impatient

1. Open a terminal, and change directories to the directory on the shared drive containing this repository.  On the ECU Macs, use the command:

    `cd /Volumes/HOME/conda_user_shared`

2. Run the setup script with the `-a` option to install everything without prompts:

    `bash conda_user_setup`

3. Exit the terminal session and open a new one to use your newly configured `conda` files.

### Detailed Instructions

The installation script has options to change directory names and locations and other parameters.  If started without options, the script is interactive and will ask the user how to proceed with each step.  Executing the script with `bash conda_user_shared -h` will show the following usage message.

    usage: $(basename $0) [-h] [-a] [-l] [-p condadir]

    Configure a ECU Physics Mac Lab computer to use conda from the command
    line and configure a (piratedrive) shared directory to contain user
    preferences and user-installed environments.  This allows the user to
    install environments once and use them on all Mac Lab computers.  Note
    that this script must be run in the users home directory (~) to install
    the symlinks in the correct location.

    Options:

      -h           Show this help message and exit.
      
      -a           Install files all links, conda initialization commands, 
                   and conda channels without prompting. This option will
                   overwrite local copies of the .conda directory and the
                   .condarc file with symlinks to the shared directory. The
                   contents of the local directory and file will be lost.
                   
      -l           Install local symlinks and initializations only. Do not
                   modify conda channels or anything in the shared
                   directory. This option will overwrite local copies of the
                   .conda directory and the .condarc file with symlinks to
                   the shared directory. The contents of the local directory
                   and file will be lost. The -l option takes precedance
                   over the -a option.
                   
      -c CONDAEXEC Set the full path to the conda executable as CONDAEXEC
                   (default: /anaconda3/bin/conda)
                   
      -d PDDIR     Set the path to the (piratedrive) shared directory with
                   the conda configuration information to PDDIR.

