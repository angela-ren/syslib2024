# Week 9 Creating a Bare Bones OPAC

## Creating the HTML Page and a PHP Search Page

1. Create a basic HTML page that contains a form for entering queries

2. Create **mylibrary.html**      `cd /var/www/html`        `sudo nano mylibrary.html` 

3. Enter html script for **mylibrary.html**



<html>
<head>
<title>MySQL Server Example</title>
</head>
<body>

<h1>A Basic OPAC</h1>

<p>In the form below,
<b>optionally</b> enter text in the search field.
You can search by author, title, or publisher.
Capitalization is not necessary.
It's okay to enter partial information,
like part of an author's, title's, or publisher's name.</p>

<p>The date fields are <b>required</b>.
You can use the date fields to limit results.
I added some extra records,
which you can view to know what you can query:</p>

<p><a href="http://34.162.161.60/opac.php">http://34.162.161.60/opac.php</a></p>

<p>This is very much a toy,
stripped down
<a href="https://en.wikipedia.org/wiki/Online_public_access_catalog">OPAC</a>.
The records are basic.
Not only do they not conform to
<a href="https://www.loc.gov/marc/">MARC</a>,
but they don't even conform to something
as simple as
<a href="https://www.dublincore.org/">Dublin Core</a>.

<p>I also don't provide options
to select different fields,
like author, title, or publisher fields.
Instead the search field below searches
all the fields
(author, title, publisher)
in our <b>books</b> table.</p>

<p>The key idea is to get a sense
of how an OPAC works, though.</p>


<h2>My Basic Library OPAC</h2>
<form method="post" action="search.php">
    <label for="search">Search:</label>
    <input type="text" name="search" id="search">
    <br>
    <label for="start_date">Start Date:</label>
    <input type="date" name="start_date" id="start_date">
    <br>
    <label for="end_date">End Date:</label>
    <input type="date" name="end_date" id="end_date">
    <br>
    <input type="submit" value="Search">
</form>

</body>
</html>

4. Create **search.php** file    `sudo nano search.php` 

 PHP Search Script:

 <?php
// Load MySQL credentials
require_once 'login.php';

// Establish connection
$conn = mysqli_connect($db_hostname, $db_username, $db_password) or
  die("Unable to connect");

// Open database
mysqli_select_db($conn, $db_database) or
  die("Could not open database '$db_database'");

// Check if search query was submitted
if (isset($_POST['search'])) {
    // Sanitize user input to prevent SQL injection attacks
    $search = mysqli_real_escape_string($conn, $_POST['search']);

    // Get the start and end dates for the date range
    $start_date = mysqli_real_escape_string($conn, $_POST['start_date']);
    $end_date = mysqli_real_escape_string($conn, $_POST['end_date']);

    // Build the MySQL query with a WHERE
    // clause that includes the date range filter
    $query = "SELECT * FROM books WHERE
        (author LIKE '%$search%' OR
        title LIKE '%$search%' OR
        publisher LIKE '%$search%') AND
        copyright BETWEEN '$start_date' AND '$end_date'";

    // Execute the query
    $result = mysqli_query($conn, $query);

    // Check if any results were returned
    if (mysqli_num_rows($result) > 0) {
        // Loop through the results and output them
        while ($row = mysqli_fetch_assoc($result)) {
            echo "ID: " . $row["id"] . "<br>";
            echo "Author: " . $row["author"] . "<br>";
            echo "Title: " . $row["title"] . "<br>";
            echo "Publisher: " . $row["publisher"] . "<br>";
            echo "Copyright: " . $row["copyright"] . "<br><br>";
        }
    } else {
        echo "No results found.";
    }

    // Free up memory by closing the MySQL result set
    mysqli_free_result($result);
}

// Close the MySQL connection
mysqli_close($conn);

echo "<p>Return to search page: <a href='http://34.162.161.60/mylibrary.html'>http://34.162.161.60/mylibrary.html</a></p>";

?>

**mylibrary.html** and **search.php** -- files are created.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/eacb612b-d0a5-4c10-bf69-8af576aa9fe3)


![image](https://github.com/angela-ren/syslib2024/assets/58860495/b97df836-90fb-455d-a079-5faf319d64e2)

5. Adding records to table: Books

- Log in MySQL  `mysql -u opacuser -p`
- Added 5 records.
- `insert into books (author, title, publisher, copyright) values`

  ('Shameen Prashantham', 'Gorillas Can Dance', 'Wiley', '2021-01-01'),
  
  ('Jack Anderson', 'Ballet & Modern Dance : A Concise History', 'Princeton Book Company', '2018'),
  
  ('Dores M.Plunk-Burdick', 'Dance Therapist in Dimension : Depth and Diversity', 'American Dance Therapy Assoc', '1974'),
  
  ('Jenefer Davies', 'Aerial Dance: A Guide to Dance with Rope and Harness', 'Routledge', '2018-09-30'),
  
  ('Hilary French', 'Ballroom: A People’s History of Dancing', 'Reaktion Books', '2022-12-10');

![image](https://github.com/angela-ren/syslib2024/assets/58860495/ca06fee5-a023-46b7-8286-138340bcb814)

6. Accessed **mylibrary.html** through the browser, and practiced searching records I entered.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/b5f4da99-4c09-44ad-bf9e-02cd3d40c51f)

7. Practiced MySQL command:
   - select * from books;
   - delete from books where author='Dores M.Plunk-Burdick';
   - insert into books (author, title, publisher, copyright) values




















