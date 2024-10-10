# Unified Practice Documentation

## Steps for Connecting to the OpenVPN Server 

1. Connect to  OpenVPN server through SSH by necessary .pem file having in our local PC(VDI)
   
Navigate to folder where .pem is located
```bash
chmod 400 <name of.pem>
```
```bash
ssh -i /path/to/<.pem file> ec2-user@<public-ip>
```
## Steps for providing VPN Access to a New Team Member
1. After logging into ec2 become root user by using
```bash
sudo su -
```
2. Add the New team-member to the openVpn server and create a password for him using
```bash
useradd <name of the new Team member>
```
```bash
passwd <name of new Team member> #(It will prompt us to enter the password)
```
3. Navigate to easy-rsa directory by using
```bash
cd /etc/openvpn/easy-rsa
``` 





