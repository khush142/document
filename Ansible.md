## 							Upcloud Disk(Storage) Document



### Adding and removing storage devices

-> The server must be powered down before attaching or removing storage devices.
		1. Start by logging into your UpCloud control panel. Shut down the server in questions and go to the Resize tab in your server settings. Create a new disk by clicking the Add new device button.
		2. In the disk configuration window, select the Create a new disk option, give the new disk a name and size in gigabytes as required. Then click Add a storage device to confirm.
		3. After the attaching process is complete, you can power the server up again.
		4. Once your server is up and running, you can continue with the command given below to type your servers terminal window in ubuntu os.

command :
		
		1. lsblk	
		2. sudo fdisk /dev/disk

-> First, start a new partition configuration with n. Use default values by just pressing enter on each of the options, or type in the required parameter if no default value is given.

		3. n
		4. a
		5. p
		6. w

-> Once fdisk has finished writing the partition table to the disk it will exit and return you to the usual command prompt. Check that the new partition shows up using the lsblk command.

		7. lsblk

-> You should now see both storage disks and their partitions with their correct sizes. The disks will be named like vda or vdb and their partitions with the added partition identifier number e.g. vda1 and vdb1. Notice that some of the commands below require you to enter the disk name while others use the partitions.

-> Set up the partition with a file system type appropriate for your server. Ubuntu and other Debian variants should use EXT4 while CentOS 7 hosts might be using XFS instead.

		8. sudo mkfs.ext4 /dev/partition  

-> With the formatting complete, you will next need to create a mounting point for the device.
Mounting a disk is as simple as making a new directory where you wish to attach the disk to, for example, /disk1 at your root directory.

		9. sudo mkdir /disk1
		10. sudo mount /dev/partition /disk1

-> The added storage space will now be available as a directory on your system.

		11. df -h

#### Detaching a disk

-> There are two ways of removing storage disks.

1. Detaching a disk simply frees the storage to be attached again and keeps the data for later use.
2. Deleting a disk removes the device from the server and deletes the data permanently.

-> Click the eject icon on the storage you wish to remove but not delete.

-> Alternatively, if you are sure to not need the device any longer, you can click the bin icon to delete the storage device permanently.

-> Once the removal operation is complete, you can start up your server again.

### Resizing storage

-> When your server is powered down, open your server settings and go to the Resize tab. At the Disks resource list, adjust the storage device size by using the slider or by entering the desired value in the text field on the right.Afterwards, just click the Save changes button to confirm the change.

-> Once the disk size has been successfully increased, the new capacity will show up at the disk information. The disk capacity indicates the storage space allocated to the device. Next, boot up your cloud server again and continue on to perform the required operations at the OS-level for Linux.

##### Increasing storage size on Linux :

-> First, check your disk and partition names with the command below.

		lsblk

-> Before making any changes, you should save the current partition table by using the next command. Note that you need to replace <disk> in the examples with the disk name you are resizing as shown in the output of the previous command e.g vda.

		sudo sfdisk -d /dev/<disk> > ~/part_table_backup.txt
	
-> After backing up the partition table, you will need to repartition the disk. Check the information of the current partition.

		sudo sfdisk -uS -d /dev/<disk>

-> Look for the start sector (probably 2048) and partition ID (probably 83) in the first partition. Then use those values in the following command in place of the bolded numbers. Note that these values are not constants, and may be different in your case. See the output of the above command for your system’s correct values.

		sudo echo "2048,,83,-" | sudo sfdisk --force -uS /dev/<disk>

-> Afterwards, reboot your server before continuing.

		sudo reboot

-> Finish the operation by running resize2fs. Notice that the <partition> means the part on the disk you are expanding. Check the output of the lsblk command if you are unsure. For example, if your disk is called vda, then your partition is probably named vda1.

		sudo resize2fs /dev/<partition>

-> You are then done! The disk should now be using all of the space allocated at the control panel. You can verify this by checking the disk size with the command below.

		df -h
		
#### Decreasing storage size on Linux :

-> Go to the Resize section in your server settings and click the Add new disk button underneath the list of your existing storage drives.

-> Select Create new disk, give the disk the required size and a name, then click the Add a disk button to confirm.

-> After the attaching process is complete, start your server up again. Once your server is up and running you can continue the resizing process at the OS level.

-> Check the name of the newly added storage disk using the following command.

		lsblk
		
-> The disk you are looking for is usually the last on the list, and will not have partitions on it like vdb in the example above. Create a new partition on the new disk using fdisk by replacing the <disk> in the command below with the new disk name.

		sudo fdisk /dev/<disk>
		
-> First, start the new partition wizard with n. Use default values by just pressing enter on each of the options, or type in the required parameter if no default value is given.

		n
		a
		p
		w
		
-> Once fdisk has finished writing the partition table to the disk it will exit and return you to the usual command prompt. Check that the new partition shows up using the lsblk -command.

		lsblk

###### Check your current disk's UUID.

sudo cat /etc/fstab

###### Replace the <UUID> in the next command with it.

sudo mkfs.ext4 -U <UUID> /dev/<partition>
	
-> Afterwards, mount the new storage disk on your system so that you can copy the files over.

		sudo mount /dev/<partition> /mnt
		
-> Install rsync if you do not already have it with

		sudo apt-get install rsync
		sudo rsync -avxHAX / /mnt

-> Once the copy process has finished, check the disk space usage to see that everything was copied. The used space will not be exactly the same, but the difference should be minimal.

		df 
		
-> Lastly, install a boot manager on the new disk so that you can boot again with a new main storage device. You need to install the correct version of GRUB depending on your system.Commonly Ubuntu and Debian use the first version.

		sudo grub-install /dev/<disk> --root-directory=/mnt --recheck

You should see a confirmation like in the example output below.

Installing for i386-pc platform.
Installation finished. No error reported.

-> After that, shut down your server either with the Shutdown request at your UpCloud Control Panel or by using the following command in your server terminal

		sudo shutdown -h now
		

With your server powered down, go to the Resize tab again and click the eject icon on the former main disk, then start up your server. Confirm that all of your data was copied successfully and is available on the new disk.

In case the server cannot find the boot section and fails to start. Shut down the server and attach the original disk again to boot from. Then reinstall the GRUB and try booting from the new disk again by detaching the old disk.
