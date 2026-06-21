scenario: application server to backup server

problem statement:

You are a cloud operation engineer managing two ec2 instances:

server A: application server
server B: backup server

the application stores its files in /data on server A. management wants a backup copy of all files on server B.

- so first we have to setup a pass less connection between two users then you have to make make directories in the server A (Application server)
- then you have to send this file to the server B (backup server) 
- for sending we can use any command scp or rsync for sending for the first time
- but for the repeated synchronization we use rsync for fast transmission and smaller bandwidth usage.
command is :
rsync -avz ./project/ ec2-user@ip:path
here ./project/ last slash is for recursive copy or internal files.
