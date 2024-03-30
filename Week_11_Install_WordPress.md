# Reflection on Installing WordPress

After following Professor Burns's instructions, I finally managed to successfully install WordPress. Prior to this, WordPress was a completely unfamiliar term to me, despite hearing it mentioned numerous times. Now, I've learned that WordPress is a free and open-source content management system (CMS) that can function as a website builder.

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






















# Install WordPress #

WordPress is completely new to me, but I heard this name many times and didn't know what its function is.

Step 2: Download and Extract


![image](https://github.com/angela-ren/syslib2024/assets/58860495/e19d63ed-94ff-43b4-8dcd-b47edd96c267)


![image](https://github.com/angela-ren/syslib2024/assets/58860495/3eb43946-a716-49de-835b-6f956edd30d9)



Step 3: Create the database and a user

![image](https://github.com/angela-ren/syslib2024/assets/58860495/9d4adb30-77d8-4367-8a21-4748d44fbe13)







Step 4: set up wp-config.php


open file using nano, add database name, user, and password

![image](https://github.com/angela-ren/syslib2024/assets/58860495/46a4019a-6c65-4f66-9ec9-a1282852725d)



Step 6: change file ownership

`sudo chown -R www-data:www-data /var/www/html/wordpress`

Step 7: Run the Install Script

![image](https://github.com/angela-ren/syslib2024/assets/58860495/95ad53fc-8176-4f43-ba53-f266b31a407d)

Password for the Test Library: bOFVY^D(81(16^8g@(
Site Title: Test Library
Username: angelaren

![image](https://github.com/angela-ren/syslib2024/assets/58860495/d196116f-425c-4ed2-b807-ba4ed646fbd0)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/22817efe-c64e-48a6-9125-86fa91027fb9)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/e0523ed9-452a-42ab-aeef-4d31ddaebd87)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/615e6b19-4e7e-4a45-ae14-05dd6d933853)












