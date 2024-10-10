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
2.
