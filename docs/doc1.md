---
id: doc1
title: RETHINKDB UPLOAD AWS S3
sidebar_label: RETHINKDB COMMAND
---

**PYTHON COMMANDSsssssss**

install pip :

		sudo apt-get install python-pip

Install the latest Boto 3 release via pip :

		pip install boto3

You may also install a specific version :

		pip install boto3==1.0.0

Executing a shell command

		os.system()

Get the users environment 

		os.environ()

**AWS COMMANDS**

Before you can begin using Boto 3, you should set up authentication credentials. Credentials for your AWS account can be found in the IAM Console. You can create or use an existing user. Go to manage access keys and generate a new set of keys :

		aws configure

Alternatively, you can create the credential file yourself. By default, its location is at ~/.aws/credentials :

		aws_access_key_id = YOUR_ACCESS_KEY
		aws_secret_access_key = YOUR_SECRET_KEY
		region=us-east-1

To use Boto 3, you must first import it and tell it what service you are going to use :

		import boto3

Let's use Amazon S3

		s3 = boto3.resource('s3')

It's also easy to upload and download binary data. For example, the following uploads a new file to S3. It assumes that the bucket my-bucket already exists :

Upload a new file

		data = open('test.jpg', 'rb')
		s3.Bucket('my-bucket').put_object(Key='test.jpg', Body=data)

**RETHINKDB COMMANDS**

Install rethinkdb : (Type all this command one by one on terminal)

		source /etc/lsb-release && echo "deb http://download.rethinkdb.com/apt $DISTRIB_CODENAME main" | sudo tee /etc/apt/sources.list.d/rethinkdb.list
		wget -qO- https://download.rethinkdb.com/apt/pubkey.gpg | sudo apt-key add -
		sudo apt-get update
		sudo apt-get install rethinkdb

Install the python driver with pip:

		sudo pip install rethinkdb

connect with rethinkdb : (It will start rethinkdb on your local server)

		rethinkdb --bind all

The RethinkDB command line utility allows you to easily take hot backups on a live cluster with the dump and restore subcommands.

Connect to the cluster at host fortress with a client port at 39500, saving to the default archive name tar.gz file (here type ip address from whom you want to take backup on fortress and typr rethinkdb port instead of 39500) (DATABASE EXPORT FROM SERVER TO LOCAL)

		rethinkdb dump -c fortress:39500 -f backup.tar.gz

Restore backup.tar.gz to the cluster running on fortress at port 39500 (DATABASE IMPORT FROM LOCAL TO SERVER)

		rethinkdb restore backup.tar.gz -c fortress:39500

Restore to the default cluster, only importing the table users to the database league from the archive backup.tar.gz

		rethinkdb restore backup.tar.gz -i league.users -c fortress:39500

Restore only specific database from backup.tar.gz

		rethinkdb restore backup.tar.gz league -c fortress:39500

overwrite the existing tar file or make new one by this command :
 
		rethinkdb dump -c fortress:39500 --overwrite -f backup.tar.gz

Send Email using python tutorial :

		https://www.geeksforgeeks.org/send-mail-gmail-account-using-python/






