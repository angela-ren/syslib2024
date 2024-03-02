# Week 8 Install and Setup a LAMP Stack
## Installing the Apache Web Server: 
- Before installing Apache, it is a good practice to update our systems first.
`sudo apt update`
`sudo apt upgrade`
- Then using `apt search` to search the specific package name - apache2
- `apt search apache2`  `apt search apache2 | head`
- 
  ![image](https://github.com/angela-ren/syslib2024/assets/58860495/3b118aee-bed4-4148-9350-3f08f38ce4bf)
  
- `apt show apache2` This command shows the package information.

- ![image](https://github.com/angela-ren/syslib2024/assets/58860495/5c0ced1b-2372-4bad-a234-6460bf4de908)

- `sudo apt install apache2` to install **apache2**

- ![image](https://github.com/angela-ren/syslib2024/assets/58860495/f7bdfa60-0aa9-42bd-9196-4db9814af845)

### Basic Checks
- This is to make sure the server is up and running configure some basic things.
  `systemctl status apache2` This command is to acquire some info about **apache2** and make sure it is enabled and running.

### Creating a Web Page
1. Text Based Web Browser
   There are a number of text based web browers available. Here using **w3m** as an example.
   `sudo apt install w3m` to install it.
   
![image](https://github.com/angela-ren/syslib2024/assets/58860495/3d98ea6d-f021-4770-a91b-4020591d1fee)

`w3m ocalhost` or `w3m 127.0.0.1` to open the browser.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/eaf96ace-6344-4396-b1c2-65a0474793e7)

2. Graphical Browser

   
3. Create a Web Page
   
   `cd /var/www/html/`
   
   `sudo mv index.html index.html.original`
   
   `sudo nano index. html`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/7cf42877-01a5-4087-8c13-bbbb74552ac7)

## Installing and Configure PHP

1. Install PHP

`sudo apt install php libapache2-mod-php`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/da7d39ed-8c01-4b25-8ab3-7725f82d85d0)

`sudo systemctl restart apache2` This command doesn't work on my computer. Having tried many times, I always got the message: 
I used this command `sudo service apache2 status` and got message "apache2 is running."

2. Check Install

`cd /var/www/html/
`sudo nano info.php` created a file called **info.php**

![image](https://github.com/angela-ren/syslib2024/assets/58860495/faeebbef-debf-4809-9b37-5d4d06bf22a1)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/11e57422-f6ff-4cdc-8440-83d9729912b5)


3. Basic Configurations
`cd /etc/apache2/mods-enabled/`   `sudo cp dir.conf dir.conf.bak`  made a backup of the dir.conf file.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/a9f8815c-d9f3-4a44-a34a-571f05de5b86)

4. Create an index.php file
`cd /var/www/html/`   `sudo nano index.php` Added the html code, the following page displayed. Not sure why.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/00908a8d-11f8-4812-bbcc-7c6852f4ed25)

## Installing and Configuring MySQL
1. Install and Set Up MySQL
`sudo apt install mysql-server` This is to install MySQL Community Server.

`mysql -u root` received the MySQL prompt
![image](https://github.com/angela-ren/syslib2024/assets/58860495/b4e7ad13-a93e-4f54-b741-4c640d913cc9)

`show databases` to request a list of the databases.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/4c161007-b904-4b0a-832d-cc2a29259f8d)

2. Create and Set Up a Regular User Account

`create user 'opacuser'@'localhost' identified by 'XXXXXXXXX';` I successfully set up a new user account.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/cd3cfa2c-22bb-4106-bc1e-b5568d701054)

3. Create a Practice Database

![image](https://github.com/angela-ren/syslib2024/assets/58860495/3fad2500-a5ea-483f-995b-9b6f17ecd90d)















`apachectl configtest` to check out configuration

![image](https://github.com/angela-ren/syslib2024/assets/58860495/140e40d3-5272-4f91-bda4-37e869b40853)

`sudo systemctl reload apache2`   `sudo systemctl restart apache2`









   


   

