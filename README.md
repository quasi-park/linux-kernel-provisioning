# A quick startup guide to constructing virtual machine
## Creating disk image
1. Open disk utility from application > others > diskutility
1. From the top left bar, choose files > New image > Create new empty diskimage
1. set the name to linux, with the partition size 8GB, use 'Apple extended Journal(case sensitive)'
1. check if disk image has been mounted to /Volumes

## Running shell script
1. move in to /Volumes/linux and run the shell script `kernel-labs.sh`.

## constructing virtual machine
1. after shell script has exited, run `vagrant init ubuntu/artful64`.
1. Use the Vagrantfile in the git. Please comment out lines 59 ~ 64 before running `vagrant up`.
1. after virtual machine has been built, `vagrant ssh` and see if virtual machine has successfully opened.
1. logout from the virtual machine.
1. uncomment the lines 59 ~ 64 in Vagrantfile, and run `vagrant reload`.
1. in `/Volumes/linux/~/Documents/`, check if `kernellabs.vdi` has been successfully made.
1. go back to /Volumes/linux and run `vagrant ssh` again.

## mounting vdi to virtual machine
1. run `sudo fdisk -l` and check if virtual disk is connected to `dev/sdb`.
1. if this is your first time booting this machine, run `sudo mkfs -t ext4 /dev/sdb`
1. in your home directory in the virutal machine, create a directory e.g)linux-kernel.
1. run `sudo mount -t ext4 /dev/sdb linux-kernel`. This will mount the vdi to linux-kernel or whatever you named your directory.

## Copying the data
1. go into linux-kernel directory.
    - TIP: if the owner of this directory has been changed to root, run `sudo chown vagrant:vagrant linux-kernel` and change back to your ownership.
1. run `cp -r /vagrant/kernel-labs .`. this will copy the git data you have downloaded previously.
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
