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
h. In the Step 2 we created username, password provide the same creds to new team-member and ask him to connect to Vpn.

## 3. Data security
### 1.GitHub:
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






