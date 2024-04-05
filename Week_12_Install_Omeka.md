

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

I spent a lot time on this **db.ini** file. Many syntax errors I encountered. Finally I got it corrected:

```; Database Configuration File
;
; Omeka requires MySQL 5 or newer.
;
; To configure your database, replace the X's with your specific
; settings. If you're unsure about your database information, ask
; your server administrator, or consult the documentation at
; <http://omeka.org/codex/Database_Configuration_File>.

[database]
host     = "localhost"
username = "omeka_user"
password = "(your own password)"
dbname   = "omeka_db"
prefix   = "omeka_"
charset  = "utf8"
```

## 4.Set file permissions:

sudo chown -R www-data:www-data files`

## 5. Restart Apache and MySQL:

`sudo systemctl restart apache2`

`sudo systemctl restart mysql`

## 6. Complete setup via web form:

![image](https://github.com/angela-ren/syslib2024/assets/58860495/61bffc10-aa9c-4848-9fbe-8ee012683d4e)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/b5adebdd-4757-426f-aca8-67c49f473b75)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/0501ccd5-2f50-4f13-b4b4-f91aa134c40e)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/40f6052c-97c7-4304-a78d-e459ad27e399)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/e005620e-72f9-453f-b682-bc26918913ac)

http://34.162.45.110/omeka/


















`







   
   
