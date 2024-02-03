# Project Title: Hosting static website on EC2 instance
# Author: Sarafadeen Ibrahim Oyinkolade.

## this project illustrate how to deploy applications on aws EC2 instances 

## . Launch an EC2 Instance:
## 1.1. Create an EC2 Instance:


Use the Amazon EC2 Dashboard to launch a new instance, selecting an Ubuntu Server AMI.
## 1.2. Configure Security Group:

Open ports 80 (HTTP) and 22 (SSH) in the security group settings.
## 1.3. Connect to Your Instance:

Use SSH to connect to your instance using the private key.
## 2. Install Nginx:
## 2.1. Update Package List:

sudo apt update
## 2.2. Install Nginx:

sudo apt install nginx
## 2.3. Start Nginx:

sudo service nginx start
## 3. Upload Your Website Files:
## 3.1. Transfer Files:

Use SCP or SFTP to upload your static website files to the server.
perl
Copy code
scp -i your-key.pem -r /path/to/your/local/site/* ubuntu@your-ec2-instance-ip:/var/www/html/
## 4. Configure Nginx:
4.1. Edit Nginx Configuration:

sudo nano /etc/nginx/sites-available/default
## 4.2. Update Root Directory:

Ensure the root directive points to the correct directory:
nginx
Copy code
root /var/www/html;
## 4.3. Save and Exit:

Press Ctrl + O to save and Ctrl + X to exit.
## 4.4. Restart Nginx:

sudo service nginx restart
## 5. Verify Website Access:
## 5.1. Visit Your Website:

Open a web browser and enter your EC2 instance's public IP or domain.
## 6. Optional Steps:
## 6.1. Secure Your Server:

Configure HTTPS using Let's Encrypt or other methods.
## 6.2. Enable Mod Rewrite (if needed):

sudo a2enmod rewrite
sudo service apache2 restart
## 6.3. Update DNS (if using a domain):

Point your domain to the EC2 instance's public IP.
Troubleshooting Tips:
Permission Issues:

If you encounter permission issues, use sudo chown -R www-data:www-data /var/www/html/.
Configuration Errors:

Use sudo nginx -t to check Nginx configuration syntax before restarting.
Firewall Issues:

Allow traffic on port 80 with sudo ufw allow 80.
Accessing Logs:

Check Nginx error logs: sudo tail -f /var/log/nginx/error.log.
Final Note:
Document Your Changes:
Keep a record of changes made to configurations, file paths, and any troubleshooting steps. This documentation will be helpful for future reference.
By following these steps and paying attention to potential issues, you can successfully host a static website on an EC2 instance with Nginx. If you encounter difficulties, refer to the troubleshooting tips and logs for guidance.
