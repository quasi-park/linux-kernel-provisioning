# A quick startup guide to constructing virtual machine
## Overview
- This repository is a semi-auto provisioning I used for the virtual machine for [this fantastic website](https://linux-kernel-labs.github.io/master/labs/index.html).
- intended for personal use only. Not to be used as commercial use.

## Prerequisites
- vagrant and virtual box, and some knowledge about them.
- macOS High Sierra. This provisioning only works for mac. Not tested on any other OS.
- some knowledge about shell script.

## Provisioning
1. Clone this repository. More specifically, you will need the Vagrantfile.
1. If you do not have vagrant or virtual box yet, you will need to download them before going on.
1. do `vagrant up` after cloning this repository.
1. do `vagrant ssh` and login to virtual machine
1. copy `kernel_labs.sh` from this directory to virtual machine home directory
1. run `./bash kernel_labs.sh`

# Running kernel-labs
1. go to directory `kernel-labs/tools/labs`.
1. run `make clean`
1. run `make boot`
1. if you see comment that look like `char device redircted to /dev/pts/1 //This is path to device`, you are done building the kernel.
1. open another shell
1. run `minicom -D PATH/TO/DEVICE`. `PATH/TO/DEVICE` is the path found in `char device redirected to ...` message.
1. login as `root`
