## 							Upcloud Disk(Storage) Document



#### Adding and removing storage devices

The server must be powered down before attaching or removing storage devices.
		1. Start by logging into your UpCloud control panel. Shut down the server in questions and go to the Resize tab in your server settings. Create a new disk by clicking the Add new device button.
		2. In the disk configuration window, select the Create a new disk option, give the new disk a name and size in gigabytes as required. Then click Add a storage device to confirm.
		3. After the attaching process is complete, you can power the server up again.
		4. Once your server is up and running, you can continue with the command given below to type your servers terminal window.

command :
		
1. lsblk	
2. sudo fdisk /dev/disk

First, start a new partition configuration with n. Use default values by just pressing enter on each of the options, or type in the required parameter if no default value is given.

3. n
4. a
5. p
6. w

Once fdisk has finished writing the partition table to the disk it will exit and return you to the usual command prompt. Check that the new partition shows up using the lsblk command.

7. lsblk

You should now see both storage disks and their partitions with their correct sizes. The disks will be named like vda or vdb and their partitions with the added partition identifier number e.g. vda1 and vdb1. Notice that some of the commands below require you to enter the disk name while others use the partitions.

Set up the partition with a file system type appropriate for your server. Ubuntu and other Debian variants should use EXT4 while CentOS 7 hosts might be using XFS instead.

## for ubuntu

8. sudo mkfs.ext4 /dev/partition  

With the formatting complete, you will next need to create a mounting point for the device.
Mounting a disk is as simple as making a new directory where you wish to attach the disk to, for example, /disk1 at your root directory.

10. sudo mkdir /disk1
11. sudo mount /dev/partition /disk1
The added storage space will now be available as a directory on your system.

12. df -h
		












