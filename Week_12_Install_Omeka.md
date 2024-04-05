# Prerequisites
Install `ImageMagick`: this is a suite of utilities to work with photo files. It's used by Omeka to create thumbnail images of any photo uploaded to the digital library.

`sudo apt install imagemagick`

Enable Apache `mod_rewrite`. This is an Apache module used to rewrite URLs. Omeka uses this to create appropriate, user friendly URLs for items and collections in its digital libraries.

`sudo a2enmod rewrite`

 Restart Apache after enabling **rewrite**

 `sudo systemctl restart apache2`

# Install Omeka

## 1. Create a new user and a new database in MySQL:
   Enter your MySQL root password when prompted.
   `sudo mysql -u root -p`
   
   `CREATE DATABASE omeka_db;`
   
   `CREATE USER 'omeka_user'@'localhost' IDENTIFIED BY 'your_password';` -----create a new password for Omeka_user acccount.

    `FLUSH PRIVILEGES;`   It ensures that the changes you've made are applied without requiring a server restart.
   
    `show databases`
   
![image](https://github.com/angela-ren/syslib2024/assets/58860495/5532d27a-2ada-4e24-8049-d0eb6e8efc29)

`EXIT;`

## 2. Download and extract Omeka:

`cd /var/www/html`

`sudo wget https://github.com/omeka/Omeka/releases/download/v3.1.2/omeka-3.1.2.zip`

`sudo apt install unzip`

`sudo unzip omeka-3.1.2.zip`

`sudo mv omeka-3.1.2 omeka` ---  rename the directory omeka-3.1.2 to omeka.

`cd /var/www/html`   `ls`   Double check the Omeka zip file is downloaded.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/166c9bae-ca07-48ab-a86d-b49f3d0e923f)

## 3. Configure database credentials:

`cd /var/www/html/omeka`

`sudo nano db.ini`

Update the db.ini file with your MySQL database credentials:

host = "localhost"

database = "omeka_db"

username = "omeka_user"

password = "your_password"  (create your own password)

## 4.Set file permissions:

sudo chown -R www-data:www-data files`

## 5. Restart Apache and MySQL:

`sudo systemctl restart apache2`

`sudo systemctl restart mysql`

## 6. Complete setup via web form:

Received an error page.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/6def8d7a-fa9f-40db-9dc8-c0bee06c442e)






`







   
   
