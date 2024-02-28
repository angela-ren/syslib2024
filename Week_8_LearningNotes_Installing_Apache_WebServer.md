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

## Basic Checks
- This is to make sure the server is up and running configure some basic things.
  `systemctl status apache2` This command is to acquire some info about **apache2** and make sure it is enabled and running.

## Creating a Web Page
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




   


   

