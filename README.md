# General

The server model is HP proLiant MicroServer Gen8.

# Config Bios for RAID1
https://www.linuxserver.io/blog/2015-03-24-setting-up-a-linux-home-server-using-the-hp-proliant-microserver-gen8-g1610t-3

https://focusedit.co.uk/40-configuring-raid-on-hp-proliant-microserver/

https://askubuntu.com/questions/524814/how-to-install-ubuntu-server-on-hp-proliant-microserver-gen8

Using RAID1 to make a mirror image of each other on the two hard disc, disc 1 and disc2. 

Hit F10 to boot into BISO --> advance --> Sata controller mode --> change from IDE to RAID.
Reboot,watch out for the RAID configuration menu and press <Ctrl>-F to configure.
On the menu select ‘LD View / LD Define Menu…. [2]’. Press <Ctrl>-C to configure the discs accordingly and save your settings.

make sure

![image](https://github.com/user-attachments/assets/bef7622e-b533-47b2-8afa-c125cb4cca01)

https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu

# Set up Ubuntu server

# Set up X-windows remote forward

```mermaid
graph LR
A[Linux<br>X Server<br>port:6000] o---o B[Linux XDMCP<br>X Client<br> UDP:177]
B o---o C[Windows<br>X Server<br>Xming<br>port:6000]
```

## Config ssh server(X Client)
/etc/ssh/sshd.config, set X11Forward to yes;

## Config ssh client
/etc/ssh/ssh_config, or ~/.ssh/config
|Source|Setup|
| ----------- | ----------- |
|Trusted|ForwardX11 yes; ForwardX11Trusted yes|
|untrusted|ForwardX11 yes; ForwardX11Trusted No|

```
startx [x client paras] ---[X server paras]
```

## port transfer
-L: local port to remote
-R: Remote port to local

ssh -N -L | -R local-port:remote-host:remote-port target

ssh -R 1678:local-host:80 firewall
Map the remote 1678 port to local web server.

# Set up NAS
Use Samba to manage NAS

```
sudo apt-get update
sudo apt-get install samba

sudo apt-get install samba-common-bin
```

To mount this NAS
```
sudo mkdir /nas
sudo smbmount -o user=, pwd= //192.168.1.111/disc /nas
```
