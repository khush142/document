#### Ansible is an open-source IT automation engine, which can remove drudgery from your work life, and will also dramatically improve the scalability, consistency, and reliability of your IT environment.

#### You can use Ansible to automate three types of tasks:

		1. Provisioning: Set up the various servers you need in your infrastructure.
		2. Configuration management: Change the configuration of an application, OS, or device; start and stop services; install or update applications; implement a security policy; or perform a wide variety of other configuration tasks.
		3. Application deployment: Make DevOps easier by automating the deployment of internally developed applications to your production systems.

#### The best part is that you don’t even need to know the commands used to accomplish a particular task. You just need to specify what state you want the system to be in and Ansible will take care of it. For example, to ensure that your web servers are running the latest version of Apache, you could use a playbook that contains the command to run apache.

#### Ansible Terms:

		1. Controller Machine: The machine where Ansible is installed, responsible for running the provisioning on the servers you are managing.
		2. Inventory: An initialization file that contains information about the servers you are managing.
		3. Playbook: The entry point for Ansible provisioning, where the automation is defined through tasks using YAML format.
		4. Task: A block that defines a single procedure to be executed, e.g. Install a package.
		ex:
		tasks:
    		- command: echo {{ item }}
      		  loop: [ 0, 2, 4, 6, 8, 10 ]
      	          when: item > 5

		5. Module: A module typically abstracts a system task, like dealing with packages or creating and changing files. Ansible has a multitude of built-in modules, but you can also create custom ones.
		6. Role: A pre-defined way for organizing playbooks and other files in order to facilitate sharing and reusing portions of a provisioning.
		7. Play: A provisioning executed from start to finish is called a play. In simple words, execution of a playbook is called a play.
		8. Facts: Global variables containing information about the system, like network interfaces or operating system.
		9. Handlers: Used to trigger service status changes, like restarting or stopping a service.

#### Install ansible in ubuntu :

		sudo apt-get install ansible

#### Check ansble is properly installed or not:

		ansible --version

#### Make ansible playbook to run yaml script by ansible :
		
example: nano nginx.yml
ansible playbook starts from --- name define the tag you want to give when file line runs. 
connection: local connect the localhost 
 ---
 - name: Install nginx
  hosts: all
  become: true
  connection: local
  tasks:
  - name: Install nginx
    yum:
      name: nginx
      state: present

  - name: Start NGiNX
    service:
      name: nginx
      state: started

#### Run ansible playbook by this command to execute file written in yml :

		sudo ansible-playbook nginx.yml



