# General

The server model is HP proLiant MicroServer Gen8.

# Config Bios for RAID1
Using RAID1 to make a mirror image of each other on the two hard disc, disc 1 and disc2. 
# Set up Ubuntu server

# Set up X-windows remote forward

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
