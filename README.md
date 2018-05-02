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
