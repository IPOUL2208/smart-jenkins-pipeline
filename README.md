Jenkins CI/CD Project on AWS (Freestyle Job)
Project Overview

This project demonstrates how to set up a CI/CD pipeline using Jenkins (Freestyle job) on an AWS EC2 Ubuntu server to automatically deploy a static website using GitHub Webhooks and Apache Web Server.

Every time code is pushed to GitHub, Jenkins automatically pulls the latest changes and deploys them to the web server.

Technologies Used

AWS EC2 (Ubuntu)

Jenkins (Freestyle Job)

GitHub & GitHub Webhooks

Apache Web Server

Git & GitHub Personal Access Token

Linux (Ubuntu)

🏗️ Project Architecture
GitHub Repo
   ↓ (Webhook)
Jenkins (Freestyle Job)
   ↓
Apache Web Server
   ↓
Static Website (Public URL)

🎯 What I Learned From This Project
🔹 Jenkins & CI/CD

Installed and configured Jenkins on Ubuntu EC2

Created and configured a Freestyle Jenkins job

Understood how Jenkins workspace works

Learned how Jenkins runs jobs as a separate user (jenkins)

Learned how Jenkins deploys files to a web server

🔹 GitHub & Webhooks

Connected a local EC2 instance to an existing GitHub repository

Used GitHub Personal Access Token (PAT) instead of passwords

Configured GitHub Webhooks to trigger Jenkins builds automatically

Debugged webhook delivery failures using GitHub “Recent Deliveries”

🔹 Apache & Linux

Installed and configured Apache on Ubuntu

Learned Apache document root: /var/www/html

Understood how file permissions affect deployments

Learned how Apache serves static content

🔹 AWS & Networking

Configured EC2 Security Groups

Opened required ports (22, 80, 8080)

Understood the importance of public IP vs private IP

Verified services using curl and system logs

🐞 Errors I Faced & How I Fixed Them
❌ 1. yum: command not found

Cause:
Used Amazon Linux commands on Ubuntu.

Fix:
Switched to Ubuntu commands:

sudo apt update
sudo apt install apache2

❌ 2. GitHub Authentication Failed

Cause:
GitHub no longer supports password authentication.

Fix:

Created a GitHub Personal Access Token

Used the token as the Git password

❌ 3. Webhook Not Triggering Jenkins

Causes Identified:

Port 8080 not open

Jenkins job trigger not enabled

Webhook misconfiguration

Fixes:

Opened port 8080 in EC2 Security Group

Enabled “GitHub hook trigger for GITScm polling”

Verified webhook delivery (HTTP 200 OK)

❌ 4. Apache Default Page Still Showing

Cause:
Jenkins was not copying files to Apache web root.

Fix:

Identified correct Apache root: /var/www/html

Fixed permissions:

sudo chown -R jenkins:jenkins /var/www/html


Corrected Jenkins build step:

cp -r * /var/www/html/

❌ 5. Changes Not Reflecting on Website

Cause:
Editing files outside Apache web root or Jenkins overwriting manual changes.

Fix:

Followed correct workflow:

Edit code → Git push → Jenkins build → Apache update


Used hard refresh / incognito to avoid browser cache

✅ Final Outcome

Successfully created a Jenkins Freestyle CI/CD pipeline

Successfully deployed a static website on AWS

Website updates automatically on every GitHub push

Fully working GitHub → Jenkins → Apache automation

🌱 Impact on My Learning Journey

This project:

Gave me hands-on DevOps experience

Helped me understand real-world CI/CD debugging

Improved my confidence with AWS, Jenkins, and Linux

Taught me how small misconfigurations can break pipelines

Prepared me for DevOps / Cloud interviews

Most importantly, I learned how to troubleshoot instead of giving up.

🚀 Future Improvements

Convert Freestyle job to Jenkins Pipeline (Jenkinsfile)

Deploy static site to Amazon S3

Add Docker for containerized builds

Secure Jenkins with authentication & HTTPS

📌 Conclusion

This project was a strong foundation in my DevOps learning journey and helped me understand how modern CI/CD pipelines work in real production-like environments.
