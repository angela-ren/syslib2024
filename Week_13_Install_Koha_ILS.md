# Install the Koha ILS #
Koha is an open source "library management system", otherwise called an integrated library system (ILS). These kinds of systems provide modules that perform specific kinds of functionality. Koha's modules include:

Administration

Patron management

Cash management

Circulation

Cataloging

Course reserves

Serials

Acquisitions

Reports

OPAC

## Google Cloud Setup ##
Creating a New Virtual Machine Instance:
Go to Google Cloud Console: Open your web browser and navigate to the Google Cloud Console.

### Create a New Virtual Machine Instance:###

Click on the hamburger ☰ icon at the top left corner.
Navigate to "Compute Engine" > "VM instances."
Click on the "Create Instance" button.
Fill in the instance details:
Name: Choose a name for your instance (e.g., koha-instance).
Region: Choose the appropriate region.
Zone: Choose the appropriate zone (e.g., us-east5-a).
Machine type: Select "Customize" and set the Series to "E2" and the Machine type to "2 vCPU, 4 GB memory."
Boot disk: Leave it as "Ubuntu 20.04 LTS."
Firewall: Ensure that "Allow HTTP traffic" is checked.
Click on the "Create" button to create the instance.

### Setting Up Firewall Rule for Port 8080: ###

Navigate to Firewall Rules:

Click on the hamburger ☰ icon at the top left corner.
Navigate to "VPC Network" > "Firewall."
Click on the "Create firewall rule" button.
Configure Firewall Rule:

Provide a name for the firewall rule (e.g., koha).
Add a description (e.g., open port 8080).
Under "Targets," select "All instances in the network."
In the "Source filter," choose "IP ranges."
In the "Source IP ranges" field, add 0.0.0.0/0 to allow traffic from any IP address.
Under "Protocols and ports," select "Specified protocols and ports."
Choose "TCP" as the protocol.
In the "Ports" field, enter 8080 to allow traffic on port 8080.
Click on the "Create" button to create the firewall rule.

## Install Koha Repo ##

Server setup

`sudo apt update`
`sudo apt upgrade`
`sudo apt autoremove -y && sudo apt clean`
`sudo apt install gnupg2`
`sudo reboot now`

When I executed `sudo reboot now`, I got an error message: host is down. It wouldn't let me continue. I spent a lot of time trying to fix, but in vain. I deleted the instance and created a new one. But I still don't know what was the problem.

angelazeng2003@koha-instance-20240411-182127:~$ sudo reboot now

![image](https://github.com/angela-ren/syslib2024/assets/58860495/61292941-bab2-4856-baeb-f38bde0e5978)


 

Add Koha Repository: 







