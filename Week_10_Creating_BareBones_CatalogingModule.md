# Creating a Bare Bones Cataloging Module #

- Create a basic HTML page that contains a form for entering bibliographic data
- The form needs to mirror the data structure in the **books** table: author, title, publisher, copyright.
- Create **index.html** page: create a new directory for this module:
   `cd /var/www/html`
  `sudo mkdir cataloging`
- Use `nano` to create the **index.html** file: `cd cataloging`  `sudo nano index.html`
- In **index.html**, add the following content:
   
<!DOCTYPE html>
<html>
<head>
    <title>Enter Records</title>
</head>
<body>
    <h1>OPAC Library Administration</h1>

    <p>This is the library administration page for entering records into the OPAC.</p>
    <p>Please do not use this page unless you are an authorized cataloger.</p>

    <form action="insert.php" method="post">
        <label for="author">Author:</label>
        <input type="text" name="author" id="author" required><br><br>

        <label for="title">Book Title:</label>
        <input type="text" name="title" id="title" required><br><br>

        <label for="publisher">Publisher:</label>
        <input type="text" name="publisher" id="publisher" required><br><br>

        <label for="copyright">Copyright:</label>
        <input type="date" id="copyright" name="copyright">

        <input type="submit" value="Submit">
    </form>
</body>
</html>


![image](https://github.com/angela-ren/syslib2024/assets/58860495/59ce079a-6315-41a3-8c2f-7a03feccd147)


- PHP Insert Script: in cataloging directory, `sudo nano insert.php`, copy the following script:

<?php

// Load MySQL credentials
require_once '../login.php';

// Establish connection
$conn = mysqli_connect($db_hostname, $db_username, $db_password) or
  die("Unable to connect");

// Open database
mysqli_select_db($conn, $db_database) or
  die("Could not open database '$db_database'");

// Prepare and bind SQL statement
$stmt = $conn->prepare("INSERT INTO books (author, title, publisher, copyright) VALUES (?, ?, ?, ?)");
$stmt->bind_param("ssss", $author, $title, $publisher, $copyright);

// Set parameters and execute statement
$author = $_POST["author"];
$title = $_POST["title"];
$publisher = $_POST["publisher"];
$copyright = $_POST["copyright"];

if ($stmt->execute() === TRUE) {
    echo "New record created successfully";
} else {
    echo "Error: " . $stmt->error;
}

// Close statement and connection
$stmt->close();
$conn->close();

echo "<p>Return to the cataloging page: <a href='http://11.111.111.111/cataloging/'>http://11.111.111.111/cataloging/</a></p>";
?>

- Security
    Create a simple authorization mechanism.
  
    `sudo htpasswd -c /etc/apache2/ .htpasswd libcat`, enter a new password at the prompt.
  
    `cd /etc/apache2/`  `ls` `sudo cp apache2.conf bak.apchje2.conf`  to save a backup copy.
  
    In the **apache2.conf** file, change the word **None** to the word **All**
  
    <Directory /var/www/>
  Options Indexes FollowSymLinks
  AllowOverride None
  Require all granted
</Directory>


<Directory /var/www/>
  Options Indexes FollowSymLinks
  AllowOverride All
  Require all granted
</Directory>

  Back to cataloging directory `cd /var/www/html/cataloging`  `sudo nano .htaccess`
  Copy the following content to  **.htaccess:`
  
![image](https://github.com/angela-ren/syslib2024/assets/58860495/5ba5976d-9d0f-410a-9056-66aa1c0864a3)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/0dbc22f1-59c0-45a6-bdfd-869d1b46b1c3)

![image](https://github.com/angela-ren/syslib2024/assets/58860495/7a677b77-381e-4bc0-b8d6-47c2d9493878)


![image](https://github.com/angela-ren/syslib2024/assets/58860495/63d040ab-5914-49dd-8233-28361c81a3f4)


![image](https://github.com/angela-ren/syslib2024/assets/58860495/824b3341-8c67-4773-a910-6484b6dd5056)

Search the book I entered:

![image](https://github.com/angela-ren/syslib2024/assets/58860495/cf527a7b-f346-4e10-93e1-c2ec4537d8ed)

Retrieved the book successfully:

![image](https://github.com/angela-ren/syslib2024/assets/58860495/e9058d41-4a58-481b-a6a9-738fa87e970f)

Use the MySQL command line interface to view the new records I entered:

![image](https://github.com/angela-ren/syslib2024/assets/58860495/bd2624fa-1320-4948-9aa4-0b45a4cf093c)




- Permissions and Ownership









