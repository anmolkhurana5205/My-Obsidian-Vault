**Nginx** (pronounced **"engine-x"**) is a **web server** that receives HTTP/HTTPS requests from clients (such as browsers) and returns web content like HTML, CSS, JavaScript, images, or API responses.

- sudo dnf update -y
-  sudo dnf install nginx -y
- nginx -t (is used to **test the Nginx configuration**.)
- service nginx status (is used to **check the current status of the Nginx service**.)
- sudo systemctl start nginx
- curl localhost