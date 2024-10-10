# Unified Practice Documentation

## Steps for Connecting to the OpenVPN Server 

1. Connect to  OpenVPN server through SSH by necessary .pem file having in our local PC(VDI)
   
Navigate to folder where .pem is located
```bash
1a. chmod 400 <name of.pem>
```
```bash
1b. ssh -i /path/to/<.pem file> ec2-user@<public-ip>
```
## Steps for providing VPN Access to a New Team Member
1. After logging into ec2 become root user by using
```bash
sudo su -
```





