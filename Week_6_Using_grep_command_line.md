# Exploring Scopus Data with Grep
## Introduction

In this document, I will show the basic use of `grep`commands to explore Scopus database related to Library and "Adult Services." I have exported 45 results as a citation file. The file name is scopus (2).bib.

## Example Grep Queries

### 1. Search for a list of `grep` commands
`grep --help` or `man grep`
This command displays a brief summary of `grep` options and their usage.
![grep commands] (Week 6_grep command line 1.JPG)
### 2. Search for an author
`grep "author={Hughes" scopus2.bib`
The command searches for entries with "Hughes" as an author. I received 1 result.
![author search] 
