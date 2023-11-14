# Nginx-Static-IP-Website

This project demonstrates how to set up a static website using Nginx and serve it on a specified domain or IP address.

## Project Overview

This simple project consists of an `index.html` file that displays a "Hello, Nginx!" message. Nginx is used to serve this static content on the specified domain or IP.

## Prerequisites

- Nginx installed on your machine.

## Setup Instructions

1. **Install Nginx:**
   - On Ubuntu or Debian-based systems, run:
     
     ```bash
     sudo apt update
     sudo apt install nginx
     ```

2. **Create Project Directory:**
   - Create a directory for your project and add an `index.html` file:
     
     ```bash
     mkdir static-website
     cd static-website
     echo "<h1>Hello, Nginx!</h1>" > index.html
     ```

3. **Configure Nginx:**
   - Create an Nginx server block configuration for your static website:
     
     ```bash
     sudo nano /etc/nginx/sites-available/static-website
     ```
     
   - Add the following configuration:
     
     ```nginx
     server {
         listen 80;
         server_name your_domain_or_ip;

         root /path/to/your/static-website;
         index index.html;

         location / {
             try_files $uri $uri/ =404;
         }
     }
     ```
     
     Replace `your_domain_or_ip` with your actual domain or IP address and `/path/to/your/static-website` with the actual path to your `static-website` directory.

4. **Create a Symbolic Link:**
   - Create a symbolic link to enable the site:
     
     ```bash
     sudo ln -s /etc/nginx/sites-available/static-website /etc/nginx/sites-enabled/
     ```

5. **Test Nginx Configuration:**
   - Before restarting Nginx, test the configuration:
     
     ```bash
     sudo nginx -t
     ```
     
     If successful, you should see a message indicating that the configuration test is successful.

6. **Restart Nginx:**
   - Restart Nginx to apply the changes:
     
     ```bash
     sudo service nginx restart
     ```

7. **Access Your Website:**
   - Open a web browser and navigate to `http://your_domain_or_ip`. You should see your static website with the "Hello, Nginx!" message.

## License

This project is licensed under the [MIT License](https://github.com/iftekharmickey/Nginx-Static-IP-Website/blob/main/LICENSE).
