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

Above diagram illustrates a typical continuous integration and continuous deployment (CI/CD) pipeline that is used to build, test, and deploy an application in an AWS environment. The workflow integrates several tools and services like GitHub, TeamCity, AWS EC2, MSSQL Server, and monitoring tools such as Amazon CloudWatch and Grafana.
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
Ensure
```bash
a.  Repo visiblity
b.  Access control based on roles
c. Two-factor Authentication
d. branch protection rules
e. Secret Management
f. Vulneribility alerts
h. Automated Security Scans
i. Audit logs
```
### 2. Vpn:


### 3. Control User access priviliges

### 4 . Antivirus software

### 5. Data Encryption

### 6. Firewall

### 7. data life cycle management







