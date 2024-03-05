# Week 9 Creating a Bare Bones OPAC

## Creating the HTML Page and a PHP Search Page

1. Create a basic HTML page that contains a form for entering queries

`cd /var/www/html` `sudo nano mylibrary.html`

html for mylibrary.html

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
