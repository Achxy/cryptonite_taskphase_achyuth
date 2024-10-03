# Comprehending Commands

### Cat
`cat` short for concatenate, is to merge multiple files (or single file) and then to stream it to standard outputs.
![not the pet I/O](../assets/not_the_pet.png)

### Catting absolute paths
Similar to the previous challenge, this time we'll invoke the `cat` command with `/flag` (which is an absolute path) as it's argument.
![catting absolute I/O](../assets/catting_absolute.png)
  
### More catting practice
Exactly the same as previous challenge, except this time the absolute path is `/usr/share/binfmts/flag`
![more catting I/O](../assets/more_catting.png)

### Grepping
Every pwn college flag begins with a `pwn.college{` boiler, we can use it as a base for our search and subsequently provide it as our first argument, the second argument is the absolute path to the file.
![grepping needle in a haystack I/O](../assets/grepping_needle_in_a_haystack.png)

### Listing files
First we need to head on over to `/challenge`, which we will do using the `cd` command, then then we'll use `ls` to list all files and folders in the current directory and we'll find the the renamed run file and execute it to get the flag.
![listing files I/O](../assets/listing_files.png)
### Touching files
### Removing files
### Hidden files

### An epic filesystem quests