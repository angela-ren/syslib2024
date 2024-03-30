# Reflection on Installing WordPress

After following Professor Burns's instructions, I finally managed to successfully install WordPress. Prior to this, WordPress was a completely unfamiliar software to me, despite hearing it mentioned numerous times. Now, I've learned that WordPress is a free and open-source content management system (CMS) that can function as a website builder.

## Installation Steps

### Step 1: Requirements Check

To ensure our systems meet the installation requirements, we checked the PHP and MySQL versions:

`sudo apt install php-curl php-xml php-imagick php-mbstring php-zip php-intl`

`php --version`

`mysql --version`

Additional PHP modules were installed to enable WordPress to operate at full functionality:

`sudo apt install php-curl php-xml php-imagick php-mbstring php-zip php-intl`

### Step 2: Download and Extract
Downloading and extracting WordPress was a straightforward process:

`cd /var/www/html`
`sudo wget https://wordpress.org/latest.tar.gz`
`sudo tar -xzvf latest.tar.gz`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/e19d63ed-94ff-43b4-8dcd-b47edd96c267)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/3eb43946-a716-49de-835b-6f956edd30d9)

### Step 3: Database Setup

We created a database and a user for WordPress:

`sudo su`   `mysql -u root`

Then, we executed the following commands within the MySQL prompt:

`create user 'wordpress'@'localhost' identified by 'XXXXXXXXX';` -- placed password (user password) in 'XXXXXXXXX'

`create database wordpress;` -- create the database name as "wordpress"

`grant all privileges on wordpress.* to 'wordpress'@'localhost';`

`show databases;`   `\q`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/9d4adb30-77d8-4367-8a21-4748d44fbe13)

### Step 4: Configure wp-config.php

We navigated to the WordPress directory and edited the wp-config.php file:

`cd /var/www/html/wordpress` --- changed to the wordpress directory

`sudo cp wp-config-sample.php wp-config.php` ----- Copy and rename the **wp-config-sample.php** file to **wp-config.php**.

`sudo nano wp-config.php` --- opened the file by using `nano`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/46a4019a-6c65-4f66-9ec9-a1282852725d)


Within the file, we updated the database name, username, and password fields. Additionally, we disabled FTP uploads by adding `define('FS_METHOD','direct');` at the end of the file.

### Step 5: Optional
We can rename the wordpress directory to something else.

For example: 

`sudo mv /var/www/html/wordpress /var/www/html/blog`  ---- change it to **blog**

The URL would look like:  `http://11.111.111.11/blog`

### Step 6: Adjust File Ownership

File ownership was adjusted to ensure proper permissions:

`sudo chown -R www-data:www-data /var/www/html/wordpress`

### Step 7: Run the Install Script

Finally, we accessed the WordPress installation page:

http://34.162.196.225/wordpress/wp-admin/install.php   

![image](https://github.com/angela-ren/syslib2024/assets/58860495/95ad53fc-8176-4f43-ba53-f266b31a407d)

However, I encountered an error page indicating no connection with the database. After spending hours troubleshooting, I discovered that the issue was caused by an incorrectly entered password in the php file.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/d196116f-425c-4ed2-b807-ba4ed646fbd0)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/22817efe-c64e-48a6-9125-86fa91027fb9)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/e0523ed9-452a-42ab-aeef-4d31ddaebd87)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/615e6b19-4e7e-4a45-ae14-05dd6d933853)


Overall, the installation process provided valuable hands-on experience.
































































