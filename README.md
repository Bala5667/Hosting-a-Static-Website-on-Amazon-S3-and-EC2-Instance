# Hosting-a-Static-Website-on-Amazon-S3-and-EC2-Instance

Primary Objectives:

To set up an EC2 instance and use an Amazon S3 bucket for storing website files, ensuring seamless website hosting. The goal was to enable public access and serve content efficiently from S3 while integrating with EC2 for web hosting.

Steps to achieve the Objectives:

1. Created an EC2 Instance (Linux) and Installed Apache Web Server
To enable web hosting on the EC2 instance, I installed Apache using the following commands:

sudo yum update –y                # Updates installed packages  
sudo yum install httpd –y         # Installs Apache Web Server  
sudo systemctl start httpd        # Starts the Apache service  
sudo systemctl enable httpd       # Enables Apache to start after a reboot  
sudo systemctl status httpd       # Checks if Apache is running  

2. Created an S3 Bucket and Uploaded Website Files
Created an Amazon S3 bucket for file storage.

Uploaded all necessary static website files (HTML, CSS, JS) to the bucket.

3. Created IAM Roles for S3 and EC2 Communication
Configured an IAM Role with S3 full access.

Attached this role to the EC2 instance to allow it to retrieve files from S3.

4. Accessed S3 from the EC2 Instance
Using SSH (Putty), I connected to the EC2 instance and executed the following commands to access the S3 bucket:

aws s3 ls                  # Lists all available S3 buckets  
cd /var/www/html/          # Navigates to Apache’s root directory  

5. Copied Website Files from S3 to EC2
Transferred files from the S3 bucket to the Apache root directory using:

aws s3 cp s3://static-website1322/ /var/www/html/ --recursive

Explanation:
aws s3 cp → Copies files from S3.
s3://static-website1322/ → Name of the S3 bucket.
/var/www/html/ → Default Apache web root folder.
--recursive → Ensures all files and subdirectories are copied.

6. Configured Apache to Serve Website Files
Set the default root folder for the Apache web server.

After copying the files from S3, accessed the website using the EC2 Public IP in a web browser.

Outcome: The website successfully loaded from the EC2 instance using files retrieved from S3.
