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

`apachectl configtest` to check out configuration

![image](https://github.com/angela-ren/syslib2024/assets/58860495/140e40d3-5272-4f91-bda4-37e869b40853)

`sudo systemctl reload apache2`   `sudo systemctl restart apache2`

4. Create an index.php file

- `cd /var/www/html/`   `sudo nano index.php`   Add some HTML and PHP to it.
  
`<html>
<head>
<title>Broswer Detector</title>
</head>
<body>
<p>You are using the following browser to view this site:</p>

<?php
$user_agent = $_SERVER['HTTP_USER_AGENT'];

if(strpos($user_agent, 'Edge') !== FALSE) {
    $browser = 'Microsoft Edge';
} elseif(strpos($user_agent, 'Firefox') !== FALSE) {
    $browser = 'Mozilla Firefox';
} elseif(strpos($user_agent, 'Chrome') !== FALSE) {
    $browser = 'Google Chrome';
} elseif(strpos($user_agent, 'Opera Mini') !== FALSE) {
    $browser = "Opera Mini";
} elseif(strpos($user_agent, 'Opera') !== FALSE) {
    $browser = 'Opera';
} elseif(strpos($user_agent, 'Safari') !== FALSE) {
    $browser = 'Safari';
} else {
    $browser = 'Unknown';
}

if(strpos($user_agent, 'Windows') !== FALSE) {
    $os = 'Windows';
} elseif(strpos($user_agent, 'Linux') !== FALSE) {
    $os = 'Linux';
} elseif(strpos($user_agent, 'Mac') !== FALSE) {
    $os = 'Mac';
} elseif(strpos($user_agent, 'iOS') !== FALSE) {
    $os = 'iOS';
} elseif(strpos($user_agent, 'Android') !== FALSE) {
    $os = 'Android';
} else {
    $os = 'Unknown';
}

if($browser === 'Unknown' || $os === 'Unknown') {
    echo 'No browser detected.';
} else {
    echo 'Your browser is ' . $browser . ' and your operating system is ' . $os . '.';
}
?>

</body>
</html>`
  
- Save the file and exit nano. In your browser, visit your external IP address site.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/b49b3515-a372-4665-bb97-6cc6331bbe4a)

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

`create database opacdb; grant all privileges on opacdb.* to 'opacuser'@'localhost'; show databases;`

From the MySQL query prompt, run this command to create a new database opacdb and to grant all privileges to opacdb to the MySQL user opacuser.

`\q` this is to exit out of the MySQL database as the **root MySQL user**, `exit`to exit out of the **root Linux user account**.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/3fad2500-a5ea-483f-995b-9b6f17ecd90d)

4. Logging in as Regular User and Creating Tables

Steps to create a table in MySQL: your can enter the command in one line or multiple lines for easy reading when creating a table. By pressing Enter key, it moves to next line with a blank prompt -> which means continuing the command line.

`mysql -u opacuser -p`   `show databases;`   `use opacdb;`

`create table books (
id int unsigned not null auto_increment,
author varchar(150) not null,
title varchar(150) not null,
copyright date not null,
primary key (id)
);`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/85eb2c70-8af9-4236-9430-016b3c725f14)

`show tables ;`
![image](https://github.com/angela-ren/syslib2024/assets/58860495/015563ae-f489-4cc9-9e0f-e0ef05d5ab78)

`describe books ;`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/341593bf-58eb-4060-b0e9-500022057e4e)

5. Adding records into the table

Steps to insert a record: 
`insert into books (author, title, copyright) values
('Jennifer Egan', 'The Candy House', '2022-04-05'),
('Imbolo Mbue', 'How Beautiful We Were', '2021-03-09'),
('Lydia Millet', 'A Children\'s Bible', '2020-05-12'),
('Julia Phillips', 'Disappearing Earth', '2019-05-14');`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/05d512ee-34ca-4eae-b30a-be9c80d1d526)

To view all the records: `select * from books ;`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/c93a2540-2e70-4081-b083-6b2916f60bda)

`alter table books add publisher varchar(75) after title;` to insert a publisher column.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/0977cb11-e5fc-4fd8-b0a6-37a77f7d6439)

To enter Publisher column data: `update books set publisher='Simon \& Schuster' where id='1';
update books set publisher='Penguin Random House' where id='2';
update books set publisher='W. W. Norton \& Company' where id='3';
update books set publisher='Knopf' where id='4';
select * from books;`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/c2668ea0-85a8-4944-9d31-dc70529ddbb2)

6. Install PHP and MySQL Support

`sudo apt install php-mysql php-mysqli`   `sudo systemctl restart apache2` `sudo systemctl restart mysql`

- Create PHP Scripts:
  `cd /var/www/html/` `sudo touch login.php` `sudo chmod 640 login.php` `sudo chown :www-data login.php` `ls -l login.php`
`sudo nano login.php`

- Scripts for login.php file:

<?php // login.php
$db_hostname = "localhost";
$db_database = "opacdb";
$db_username = "opacuser";
$db_password = "XXXXXXXXX";
?>

- Create a new PHP file for our website. This file will display HTML but will primarily be PHP interacting with our books database.
`sudo nano opac.php` to create a file called **opac.php**.

Scripts:

<html>
<head>
<title>MySQL Server Example</title>
</head>
<body>
<h1>A Basic OPAC</h1>
<p>We can retrieve all the data from our database and book table
using a couple of different queries.</p>
<?php
// Load MySQL credentials
require_once 'login.php';
// Establish connection
$conn = mysqli_connect($db_hostname, $db_username, $db_password) or
  die("Unable to connect");
// Open database
mysqli_select_db($conn, $db_database) or
  die("Could not open database '$db_database'");
echo "<h2>Query 1: Retrieving Publisher and Author Data</h2>";
// Query 1
$query1 = "select * from books";
$result1 = mysqli_query($conn, $query1);
while($row = $result1->fetch_assoc()) {
    echo "<p>Publisher " . $row["publisher"] .
        " published a book by " . $row["author"] .
        ".</p>";
}
mysqli_free_result($result1);
echo "<h2>Query 2: Retrieving Author, Title, Date Published Data</h2>";
$result2 = mysqli_query($conn, $query1);
while($row = $result2->fetch_assoc()) {
    echo "<p>A book by " . $row["author"] .
        " titled <em>" . $row["title"] .
        "</em> was released on " . $row["copyright"] .
        ".</p>";
}
// Free result2 set
mysqli_free_result($result2);
/* Close connection */
mysqli_close($conn);
?>
</body>
</html>

- Save the file and exit out of `nano`.
- `sudo php -f login.php`  `sudo php -f index.php`  to test the PHP syntax.

Display on a webpage: external IP address/opac.php

![image](https://github.com/angela-ren/syslib2024/assets/58860495/058c6752-93c3-4ac6-9af0-35195b551d65)

[Week 8 Learning Notes] (https://github.com/angela-ren/syslib2024/blob/main/Week_8_LearningNotes_Installing_Apache_WebServer.md)

































   


   

