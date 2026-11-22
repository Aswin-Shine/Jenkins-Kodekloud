The DevOps team at xFusionCorp Industries is initiating the setup of CI/CD pipelines and has decided to utilize Jenkins as their server. Execute the task according to the provided requirements:

1. Install Jenkins on the jenkins server using the apt utility only, and start it using the service command. The jenkins server runs Ubuntu without systemd (systemctl does not work there), and current Jenkins releases need Java 21 or later (for example openjdk-21-jre).

If you face a timeout issue while starting the Jenkins service, first check the service status with service jenkins status
Then review the logs in /var/log/jenkins/jenkins.log to identify the cause.
2. Jenkin's admin user name should be theadmin, password should be Adm!n321, full name should be Yousuf and email should be yousuf@jenkins.stratos.xfusioncorp.com.

Note:

1. To access the jenkins server, connect from the jump host using the root user with the password S3curePass (if it is refused right after the lab starts, wait a minute: the server is still being prepared).

2. After Jenkins server installation, click the Jenkins button on the top bar to access the Jenkins UI and follow on-screen instructions to create an admin user.

Solution : 

1. SSH into the Jenkins Server and update the server
```
ssh root@jenkins 
apt update -y 
```

2. Install Java and Jenkins
```
apt install -y openjdk-21-jre fontconfig curl gnupg

install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key -o /etc/apt/keyrings/jenkins-keyring.asc
chmod a+r /etc/apt/keyrings/jenkins-keyring.asc
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" > /etc/apt/sources.list.d/jenkins.list
apt update && apt install -y jenkins
```

3. Start the jenkins server and check for the service logs. 
```
service jenkins start

service jenkins status
tail -n 100 /var/log/jenkins/jenkins.log
```

4. Open the jenkins ui and create the user. 