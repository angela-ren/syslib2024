# Week 7 Managing Software
## `sudo` command: the sudo command "executes a command as the superuser". The name of the superuser account is root. 
`sudo apt update`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/64707481-4837-478e-8702-84eabbd938ce)

## `apt` command
`apt search tldr` tldr is a community-driven application that provides simple help pages and examples of how to use some commonly used commands.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/b8cf4c40-d7ee-4375-8562-58627f785c6d)

`apt show tldr`

![image](https://github.com/angela-ren/syslib2024/assets/58860495/746b18d5-7773-4a7c-8991-d7a223eca11f)

`sudo apt install tldr` This command is to install the application.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/d69713e8-b83c-44ec-bf48-b091ce40f770)

`sudo apt --purge remove tldr` This commande is to remove system configuration files.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/fd17dbac-d2f5-4811-ac1c-51f49d5d1d61)

`sudo apt autoremove`to uninstall applications.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/39f6794c-4cdd-4542-aeac-9f0964561eb6)

`sudo apt clean` This command removes those extra files and frees up disk space.

## Library Search
### Installing yaz
`apt search yaz`-- search for the software called `yaz`.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/f9d483a7-3da9-49b3-8bf6-a03c624f392a)

`apt show yaz`- to get information about the software.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/0549d41b-b07b-4bdc-b4c6-4f8ce3f484d2)

`sudo apt install yaz` - to install the software.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/4e39325a-ce8c-47d3-ba72-b10c36f8e3a9)

### Documentation
`man yza-client` This is to access its manual page.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/d7f36692-0ad1-4a0c-aa0f-f7f3bde98d05)

`man bib1-attr` for attribute documentation.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/7003225b-5220-4cb3-8472-def2c3d0b128)

### Using `yaz`
`yaz-client` Opening yaz-client receives a separate command line interface with a new prompt: Z>

![image](https://github.com/angela-ren/syslib2024/assets/58860495/3618d10b-be83-43bf-a673-d0e649441679)

Use `open` command followed by the server address:
open saalck-uky.alma.exlibrisgroup.com:1921/01SAA_UKY
![image](https://github.com/angela-ren/syslib2024/assets/58860495/632bf559-05b7-4cdf-afb2-3e133c7a97fc)

### Queries
Example 1: To find title with word "information" and the Library of Congress Subject Heading "library science".
`find @and @attr 1=4 "information" @attr 1=21 "library science"` 
The search does not reveal the results. To peruse the results, we use the show command. `show 6` to show the 6th record.
In the above:
- `find` is the command that sends a search request
- `@and` is the operator signifying a Boolean AND search of multiple attributes
- `@attr 1=4` instructs the query to search for the term in the Title
- `"information"` is the first search term for the Title search
- `@attr 1=21` instructs the query to search for the term in the Subject-heading
- `"library science"` is the second search term for the subject heading search

![image](https://github.com/angela-ren/syslib2024/assets/58860495/dade965c-99f8-418e-bbf3-42d7187c8f7b)

Example 2: Find with subject headings "library science" and "philosophy"
`f @and @attr 1=21 "library science" @attr 1=21 "philosophy"`

Example 3: Find where personal name is "mcmurtry, larry"
`f @attr 1=1 "mcmurtry, larry"`

Example 4: Find any for "c programming language"
`f @attr 1=1016 "c programming language"`



















