interview question - create a new user (not root) and give him access.

first create a new user into your system.
sudo adduser username (to make new user).
set password for the new user.
su - username (to switch to new user).
then in the new user create .ssh folder and create file named "authorized_keys". 
then told the person to generate key pairs in its computer and send its public key to you (this is much safer option).
then you have to store his public key in newly created "authorized_keys" file.
now from your side the task is done you gave access to someone successfully.
now the user simple login using the cmd "ssh user_name@public_ip" logged in. 
