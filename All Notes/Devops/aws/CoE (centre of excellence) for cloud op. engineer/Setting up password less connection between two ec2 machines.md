interview question - how to setup password less connection between two ec2 servers. login from server1 to server2

ssh-keygen -t rsa (to generate keys first step for password less connection setup)

two keys were generated in .ssh folder of the server 1.
you have to copy the public key to the authorized keys file in the server 2.
then for login from server 1 with the below cmd.

command for login : ssh ec2-user@private_ip_of_server which we want to connect (for password less connection btw two ec2 machines)
