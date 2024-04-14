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

## Install Koha ##

`apt update`  should be `sudo apt update`

`sudo apt show koha-common`  The command downloads and installs a lot of additional software, and therefore the process takse several minutes.

## Configure Koha ##

`sudo nano /etc/koha/koha-sites.conf`

change the line that contains the following information: INTRAPORT="80"  to  INTRAPORT="8080"

Install and setup mysql-server:

`sudo apt install mariadb-server`

 Need to enable URL rewriting and CGI functionality
 
`sudo a2enmod rewrite`
`sudo a2enmod cgi`

`sudo systemctl restart apache2`   Restart Apache2 to apply the changes.

Create a database for Koha: `koha-create `create-db bibliolib`

Configure Apache2 to Listen on Port 8080: `sudo nano /etc/apache2/ports.conf`

  - Add Listen 8080 at the end of the file. Save the file and exit the text editor.
  - `sudo apachectl configtest` to check if the Apache configuration changes are valid

![image](https://github.com/angela-ren/syslib2024/assets/58860495/1527bcb6-a187-4ef5-95a4-0523ae1389e1)
 
  - Restart `sudo systemctl restart apache2`

Disable Default Apache2 Setup and Enable Bibliolib Site: Run the following commands:

`sudo a2dissite 000-default`   
`sudo a2enmod deflate`   
`sudo a2ensite biblioli`   
`sudo systemctl reload apache2`   
`sudo systemctl restart apache2`   

## Koha Web Installer ##

 - Open the koha-conf.xml file using the nano text editor: `sudo nano /etc/koha/sites/bibliolib/koha-conf.xml`

 ![image](https://github.com/angela-ren/syslib2024/assets/58860495/28b414b1-7614-464d-bc3a-de3c3d50152e)

 - Write down the username and password
 
 http://34.162.150.82:8080

Koha installation process (https://koha-community.org/manual//22.11/en/html/installation.html)
 
 
![image](https://github.com/angela-ren/syslib2024/assets/58860495/d79deb8b-e700-49be-9764-9f40c109a1e2)


Database settings

![image](https://github.com/angela-ren/syslib2024/assets/58860495/7f917e49-e299-4e92-8182-9bc6c3b3a2bd)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/62f89cf3-432c-42c3-95ad-4f4cda010c9c)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/87998f89-6fff-4ddb-8c87-8c7173ccfb42)


![image](https://github.com/angela-ren/syslib2024/assets/58860495/bb159cb9-7d8e-4652-9705-537927a48cc8)


![image](https://github.com/angela-ren/syslib2024/assets/58860495/699640d8-0e6d-459f-a0a6-535fa47825a9)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/b6d2a7e8-3ed8-4d11-a9cd-6cbe3a10ae8c)


OPAC http://34.162.150.82:8080/cgi-bin/koha/mainpage.pl


















