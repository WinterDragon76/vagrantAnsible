# vagrantAnsible

This code should be run on a Linux machine. I'm using Kali Linux but any Linux machine will suffice.

The hardening tasks will be to add a login screen for authorised users only, update patching and remove unwanted packages.

To run this installation, Install VirtualBox on the Linux machine machine, • Install Ansible on the Linux machine machine, • Install Vagrant on that Linux machine machine.

You will then • Run the VagrantUp for AlmaLinux • Build an Ansible playbook and configure Vagrant to use Ansible provisioning

After installing Virtual Box, Vagrant and Ansible onto the host Linux machine, open a terminal and log in as root: sudo -s

Create the directory: mkdir ansible-book && cd ansible-book

Create a vagrantfile: Vagrant init almalinux/8

A vagrant file is then created. Some modifications were then made to: • Enable GUI (If this is not set, the vagrant up freezes and times out as there is a section in the launch that requires a selection) • Port forwarding • Extend the timeout – as my machine is older, it needs a bit of extra time to run • Nominate Ansible as the provisioning tool.

Create a subdirectory for the ansible provisioning: mkdir provisioning && cd provisioning

Create the issue text file – this will be used as the text for the login screen. cat > issuePAGE 4 Ctrl + D to save. cat > playbook.yaml

Use VSCode to modify the above two files. In the “issue” file, I created a generic Authorisation warning stating that it to be accessed by authorised people only.

In the “playbook” file, this is where I created the Ansible Playbook.

To start the vagrant machine, type in: vagrant up

Vagrant will then check to see if there is an existing instance of the vagrant box for the distribution specified. If it is not present, it will download it. This will take some time. Once it is downloaded, any time “vagrant up” is run, it will launch from this predownloaded directory. As the GUI was enabled, during the vagrant up, a GUI of the machine will launch. When it prompts to select the distribution, clicking the spacebar or clicking in the screen will select this and continue the setup. Once launched, the terminal will return to the prompt and you can check the status by typing: vagrant status

During the “vagrant up” vagrant will have looked in the provisioning sub-directory for the ansible playbook and started running the tasks. The tasks will show what was nominated as the “name” and the status of the task. When this has successfully launched, the remaining playbook tasks were added and tested. After each was set up, to test the new playbook tasks, I ran: vagrant provision

For the login warning message, the playbook will look within the provisioning directory for the text file called “issue”.

To delete the Virtual Machine when done with it, type: vagrant destroy And select “Y”.

You can then simply type “vagrant up” to provision as many identical machines as you like
