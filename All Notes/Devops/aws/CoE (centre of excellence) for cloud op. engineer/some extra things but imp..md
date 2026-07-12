
echo "this is the content" > file_name (for overwritten)

echo "this is the content" >> file_name (for append)

ls -a (show hidden files also)

ls -l (long format)

pwd (to print working directory)

scp file_name ec2-user@ip:path (when passless connection is already estab. btw two ec2 machines then for sending files)
scp -i "key_name.pem" file_name ec2-user@ip:path (when connection is not already estab. btw two ec2 machines then for sending files)

ssh -i "key_name.pem" ec2-user@ip (this is passwordfull connection)

cat file_name (for viewing file content)

vi file_name (to open editor)

there are two modes in this insert mode and normal mode (command mode)
when you are in normal mode write i to enter into the insert mode. to confirm you are in insert mode you will see --insert-- at the bottom.
when you are in cmd mode(normal mode) write colon (:) and write one word command like w for saving, q for exit.

curl - `curl` (Client URL) is a **command-line tool used to send requests to a URL and receive the response**. It's commonly used to test APIs, websites, and web servers.
ex - curl localhost




difference between rsync and scp ?

what is cron tab ?

vpc setup pending ...




connection to IAM role