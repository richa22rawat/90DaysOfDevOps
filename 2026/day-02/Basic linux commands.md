Baics commands  

Navigation commands -

1. ls - list all files and directories.
2. ls -l - Shows detailed information like permission,owner, size, and date.
3. ls -a - show all files including hidden files. Hidden files in Linux usually begin with a dot (.), such as .bashrc.
4. ls -lh - Shows detailed information with human-readable file sizes, such as KB or MB
5. ls -la - Shows all files, including hidden files, in detailed format
6. ls /home/ubuntu - list Ccontent of a specified directory.
7. pwd - shows your current directory.
8. cd - change directories 
9. cd .. - move one directory up/ back
10. cd ~ - goes to home directory
11. cd / - goes to root directory
12. clear - clears the terminal

Create files and directories

1. touch - creates an empty file. eg. touch notes.txt
2. mkdir - creates a new directory. eg.mkdir practice
3. mkdir -p - Creates nested directories. eg. mkdir -p DevOps/Linux/Day1
4. cp - Copies a file. eg. cp notes.txt backup.txt
5. cp -r - Copies a directory and its contents eg. cp -r practice practice_backup
6. mv - Moves or renames a file/directory eg. mv notes.txt linux.txt
7. rm - deletes a file eg. rm notes.txt
8. rmdir - Deletes an empty directory eg. rmdir practice
9. rm -r - Deletes a directory and its contents recursively eg. rm -r practice_backup

View and read file contents

1. cat - displays file contents
2. less - Views long files page by page
3. more - Views content page by page
4. head - Shows the first 10 lines by default
5. head -n 5 - Shows the first 5 lines
6. tail - Shows the last 10 lines by default
7. tail -n 5 - Shows the last 5 lines
8. tail -f - Follows new lines added to a file	, particularly useful for watching application logs in real time.

Write and display text

1. echo - print text in terminal
2. echo > - Writes text to a file, replacing existing content
3. echo >> - Adds text to the end of a file
4. nano - Opens a simple terminal text editor, if installed

Find files and search text

1. find - Finds files and directories by criteria eg. find . -name "notes.txt"
2. grep - Searches for text inside files eg. grep "error" app.log
3. grep -i - Searches without case sensitivity 
4. which - Shows the executable path for a command 
5. file - Identifies a file's type eg. file notes.txt

Understand files and disk space

1. stat - Shows detailed file metadata eg. stat notes.txt
2. wc - Counts lines, words, and bytes eg. wc notes.txt
3. du -sh - Shows the total size of a directory eg. du -sh practice
4. df -h - Shows filesystem disk usage eg. df -h

Basic permissions and identity

1. whoami - Shows the current username
2. id - Shows user and group IDs
3. groups - Shows the groups a user belongs to
4. chmod - Changes file permissions eg. chmod 644 notes.txt
5. chown - Changes file ownership; usually requires elevated privileges eg. sudo chown ubuntu:ubuntu notes.txt

Get help and check command history

1. man - Opens a command's manual eg. man ls
2. ls --help - Displays command help
3. history - Shows previously executed commands
4. date - Shows the system date and time
5. cal - Displays a calendar, if installed
6. uname -a - Shows kernel and system information




