---
id: doc3
title: BASIC COMMAND OF LINUX
---
#### sudo : It is a root command gives permission to root user.
			sudo su

#### ls : This command display all file and folder that you currently working on.
			ls

#### cd : use to change the working directory.
		cd directory_name

#### mkdir : used to make new directory/folder.
			mkdir directory_name

#### rmdir : remove directory which is empty
			rmdir directory_name

#### cp : copy and paste from one folder to another
			cp file_name destination

#### rm : This is use to remove file.
			rm -r file_name

#### apt-get : This command is use to install/update/upgrade the software from your device.For that you need root permission.
			sudo apt-get software_path

#### grep : This is use to find out the exact location or path if you don't know where your file is situated.
			grep file_name

#### cat : This command is use to show the text written in your file
			cat file_name

#### poweroff :
			This command is used to directly power off your device from terminal

#### pwd :
			This is used to show which directory you are currently in

#### exit :
			exit from root directory as well as terminal.

#### df :
			This is used to show the disk space storage.
			df -h : Show in terms of bytes

#### free :
			This is used to show the free available memory space.
			free -m : show free memory in terms of bytes rather than blocks

#### top :
			This command will give all information about OS (CPU,RAM)

#### uname -a :
			This gives all info about system name,kernal name,version

#### lsb_release -a :
			This will show the version of ubuntu used.

#### ls -l file_name :
			To see which permission is given to selected file

#### chmod 762 file_name : change permission
			1st : Owner 2nd : GroupUser 3rd : Public
			1 : Execute
			2 : Write
			4 : Read  

#### To copy file from local device to remote device
			rsync -zaP ~/Desktop/projects/my-file hostname@ip-add:~/home/  

#### To exclude some file
			rsync -avz --exclude 'file or folder name' sorce/destination

#### Export database
			mysqldump -u root -p databasename > backup.sql (file-name you wish to copy your database)

#### Import database
			mysql -u root -p databasename < backup.sql

#### ctrl+shift+D :
			Return from MYSQL terminal
