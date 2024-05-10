# project-jenkin

How to Deploy a Website on EC2 Using Jenkins:

    https://blog.devops.dev/how-to-deploy-a-website-on-ec2-using-jenkins-f2b32fdc0655 

Create an EC2 Instance

Launch an EC2 ubuntu instance 22.04/t2/micro/ssh/http/https-anywhere/8gb

connect ec2 instance

    sudo apt update

Create on GITHUB repo and add index.html file

Install Jenkins:

    sudo apt install fontconfig openjdk-17-jre -y
    java -version
    sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
    https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null
    sudo apt-get update
    sudo apt-get install jenkins -y
    sudo systemctl enable jenkins
    sudo systemctl start jenkins
    sudo systemctl status jenkins

Login to the Jenkins and Create a new freestyle project named “website development.”

Configure Jenkins Job

Configure the job with the following details:

— Description: Website Development with Jenkins freestyle job

— Source code: Git (Paste GitHub repository URL)

— Select the required branch.

In buid step -> Add build step -> Execute shell -> 

Copy and paste the following commands into the command box:

```bash
sudo apt install -y git
sudo apt install -y apache2
sudo systemctl start apache2
sudo systemctl enable apache2
sudo rm -rf /var/www/html
sudo git clone <github_repository_url> /var/www/html
```

Click on Save to save the job configuration and Trigger the Jenkins Job.

Access the Deployed Website (e.g., http://<aws_public_ip_address:8080>)



