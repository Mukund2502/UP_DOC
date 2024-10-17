# Unified Practice Documentation

## 1. Steps for Connecting to the OpenVPN Server 
a. Connect to  OpenVPN server through SSH by necessary .pem file having in our local PC(VDI)

   Navigate to folder where .pem is located
```bash
chmod 400 <name of.pem>
```
```bash
ssh -i /path/to/<.pem file> ec2-user@<public-ip>
```
## 2. Steps for providing VPN Access to a New Team Member
a. After logging into ec2 become root user by using
```bash
sudo su -
```
b. Add the New team-member to the openVpn server and create a password for him using
```bash
useradd <name of the new Team member>
```
```bash
passwd <name of new Team member> #(It will prompt us to enter the password)
```
c. Navigate to easy-rsa directory by using
```bash
cd /etc/openvpn/easy-rsa
``` 
d. Generate Client certificate and private key for the new team-member without requiring a password for the key using
```bash
./easyrsa build-client-full <new team-member name> nopass
```
e. Copy the contents of Client certificate(.cert) and private key(.private.key) by navigating to
```bash
cd pki/issued 
cd pki/private
```
f. Create a .ovpn profile for new team-member by properly mentioning below content in the .ovpn file
```bash
```
g. Place the .ovpn file under the below path

   For windows
```bash
C:\Program Files\OpenVPN\config
```
   For MacOs
```bash
~/Library/OpenVPN #(or you can simply drag and drop the .ovpn file onto the Tunnelblick icon)
```
h. In the  **Step 2** we created username, password provide the same creds to new team-member and ask him to connect to Vpn.


##  Deployment Diagram
![deployment](https://github.com/user-attachments/assets/f9ab23af-5f72-4068-8168-fd567c583e32)

Above diagram explains a typical continuous integration and continuous delivery (CI/CD) pipeline that is used to build, test, and deploy an application in an AWS environment. The workflow integrates several tools and services like GitHub, TeamCity, AWS EC2, MSSQL Server, and monitoring tools such as Amazon CloudWatch and Grafana.
### Workflow Explanation:
#### 1. Source Code Management with GitHub:

The process starts with the developers pushing their code to GitHub, a source code management platform.
The version control system used here is Git, which helps track changes and manage the code base.
#### 2. TeamCity as the CI Server:

TeamCity Server pulls the code from GitHub.
The server orchestrates the build process by distributing tasks to one or more TeamCity Agents.
TeamCity Agent is responsible for running the build tasks, which include compiling the code, running automated tests, and preparing the application for deployment.
Once the code is successfully built and tested, the TeamCity Server pushes the build artifacts to the deployment stage.
#### 3 . Deployment to AWS EC2:

After the build is complete, the application is deployed onto an EC2 instance in the us-east-1a availability zone within the N. Virginia region of AWS Cloud.
The EC2 instance hosts the application and connects to other services, such as the database.
#### 4. Database Integration (MSSQL):

The application on EC2 communicates with an MSSQL Server hosted either on the same EC2 instance or on another instance. This server handles data storage, management, and retrieval.
MSSQL (Microsoft SQL Server) is the database engine responsible for the relational data used by the application.
#### 5. Monitoring and Logging:

CloudWatch is connected to monitor the EC2 instance and the MSSQL server. It collects logs and metrics related to the application's performance, resource usage, and health.
Grafana is used for advanced data visualization and real-time monitoring. It pulls data from CloudWatch or directly from the MSSQL database to provide insights into the application's health and performance.





## 3. Data security
### 1.GitHub:
#### a.  Repo visiblity 
Ensure repo is pvt.
#### b.  Access control based on roles
Ensure acess is provided based on the role of the team-member
#### c. Two-factor Authentication
For additional security enable two-factor authentication by navigating to **https://github.com/settings/security**
#### d. branch protection rules
Set branch protection rules so that we can prevent direct pushes to branches, restrict pushes and it enhances code quality by having multiple code reviews.
#### e. Secret Management
In order to ensure  sensitive data such as API keys and passwords, is protected from unauthorized access and potential breaches we need to make sure that we are implementing this in our codebase.
#### f. Vulneribility alerts
Enable Dependabot alerts so that we will receive alerts for vulnerabilities that affect our dependencies and manually generate Dependabot pull requests to resolve these vulnerabilities.
#### h. Automated Security Scans
Do security scans for repo,secrets  by using code scanning and secret scanning.

### 2. Vpn:
In our project, we are using OpenVPN, which provides a secure and encrypted connection to our AWS environments. This setup ensures secure client connections, authenticates users, and routes traffic safely.

### 3. Control User access priviliges
Based on the role of team-member we need to ensure that we are providing right level of access for all the tools and technologies for smooth workflow.(i.e, github,aws,Teamcity server) 

### 4 . Antivirus software
Frequent scanning of our VDI's and systems is mandated so that from our end we are ensuring that any potential threats or vulnerabilities are detected and addressed promptly. For this we came up with an open source tool called malware bytes and we can download this from **https://www.malwarebytes.com/mwb-download**

### 5. Firewall
In Unified practice we are using aws WAF which helps us to  safeguard our web applications from common web exploits and vulnerabilities that could affect application availability, compromise security.

### 6. Data life cycle management
In our project, we created  **AWS Data Lifecycle Manager** to automate the creation, retention, and deletion of EBS snapshots and AMIs. This service helps us manage our data more efficiently, ensuring that backups are consistently updated and also we can optimize storage costs by removing unnecessary data. By implementing lifecycle policies, we enhance our data security posture by ensuring that our critical data is properly backed up and that outdated data is securely removed.







