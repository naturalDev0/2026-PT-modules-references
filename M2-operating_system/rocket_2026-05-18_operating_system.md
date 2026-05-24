# Recap - 2026 May 18 - Operating System

## Linux

## Terminal

### Commands

```bash
# print current working directory path
pwd

# list all files/folders of current working directory
ls
ls -l
ls -la

# change directory
cd
# e.g. navigate to
cd ./important_documents/
# current directory
cd .
# one level above from current directory
cd ..

# copy files/folders
cp `source_file` `destination_path`
cp .env ./another_folder/.env
cp index.js index-2.js

# move file/folder to another location
mv main/ ../children/
# OR rename file/folder within the same working location
mv calculations.js numbers.js

# create directory/folder
mkdir
mkdir utility

# remove file
rm
# remove folder recursively
# all files and subdirectories are deleted
rm -r
# remove directory/folder
rmdir

# create a new file without any contents within
touch
touch reminder.txt

# preview the contents within the file
cat
cat home.html
```