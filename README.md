# A quick startup guide to constructing virtual machine
## Overview
- This repository is a semi-auto provisioning I used for the virtual machine for [this fantastic website](https://linux-kernel-labs.github.io/master/labs/index.html).
- intended for personal use only. Not to be used as commercial use.

## Prerequisites
- vagrant and virtual box, and some knowledge about them.
- macOS High Sierra. This provisioning only works for mac. Not tested on any other OS.
- some knowledge about shell script.

## Provisioning
1. clone this repository. `git clone https://github.com/quasi-park/linux-kernel-provisioning.git`
1. run `./kernel_labs.sh`
1. run `vagrant ssh` and cp `run_in_vm.sh` to virtual machine.
1. run `./run_in_vm.sh`
1. go into the directory and enjoy kernel labs :)
    - TIP: you might want to `make clean` at `tools/labs` before doing `make boot`

## After booting...
1. there are many ways to continue from here. This is one possible way.
1. in terminal, use command `tmux`.
    - [how to use tmux(Japanese :))](https://qiita.com/vintersnow/items/be4b29652ff665c45198)
    - TIP: THe default keybind is CTRL + b. `CTRL+b c` opens new shell.
1. in tmux shell, make boot.
1. When make boot is loaded, you will find a log saying something like `char device redirected to /dev/pts/2`. Use the screen command on the other tmux shell, and run `screen /dev/pts/2` or whatever your make boot redirected to.
1. by using the screen command, you will be able to use the virtual machine.
    - [How to use screen(japanese :))](https://qiita.com/ryounagaoka/items/8203e9c149b542986c92)

## If you logged out or shutdown your pc...
1. Your dmg will be de-mounted, so you have to re-mount your dmg again.
1. To do so, you will need to find your dmg in the place where you saved.
    - TIP: by default, dmgs are saved under ~/Documents. Or you can always use spotlight to spot files.
1. after mounting the dmg, go back to `/Volumes/[your dmg]`.
1. you need to `vagrant up` again.
1. you also need to `sudo mount -t ext4 /dev/sdb linux-kernel` again.
1. check if everything is restored.
