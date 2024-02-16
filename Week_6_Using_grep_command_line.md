# Exploring Scopus Data with Grep
## Introduction

In this document, I will show the basic use of `grep`commands to explore Scopus database related to Library and "Adult Services." I have exported 45 results as a citation file. The file name is scopus2.bib.

## Example Grep Queries

### 1. Search for a Llist of `grep` Commands
`grep --help` or `man grep`
This command displays a brief summary of `grep` options and their usage.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/4d30ad2a-d4c6-4938-83ba-ef5684d6ad4c)

### 2. Search for an Author
`grep "author={Hughes" scopus2.bib`
The command searches for entries with "Hughes" as an author. I received 1 result.
![image](https://github.com/angela-ren/syslib2024/assets/58860495/b0933104-5185-4308-8670-7e54b8f3d283)

### 3. Search for Publications on a Specific Topic
`grep -i "Library Services" scopus2.bib`
This command searches for enries with "Library Services" in the title (case matching). I received 1 result.

![image](https://github.com/angela-ren/syslib2024/assets/58860495/f4cbbfbd-a189-48da-9718-2374840f1800)

`grep -i "title.*library service" scopus2.bib` This command looks for the title contains the exact phrase "library service".
![image](https://github.com/angela-ren/syslib2024/assets/58860495/b04c1708-1a5f-46ec-b727-db857e0f5154)

### 4. Publication Year
`grep -i "year = {2019}" scopus2.bib` This command searches for lines where the year field contains "2019".
![image](https://github.com/angela-ren/syslib2024/assets/58860495/2002079b-6d61-4251-b4f6-b2af51ddccba)

### 5. Search for a Specific Journal
`grep "journal = {Library Trends}" scopus2.bib`  This command searches for entries published in the "Library Trends" journal.
![image](https://github.com/angela-ren/syslib2024/assets/58860495/5bdda815-ae24-4504-a76a-258839428c1a)

### Summary
Learning the basics of `grep` has been interesting for me, although I find it hard o remember the commands. Still, I see how `grep` is useful for exploring big sets of data and retrieving the data I need.




