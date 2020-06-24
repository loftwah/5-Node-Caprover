# Install/Configure 5 VM's (I used Proxmox/Ubuntu 18.04 VM's)

* #### Enable Passwordless Sudo (optional)

```
sudo nano /etc/sudoers
Find the line which contains #includedir /etc/sudoers.d
Below that line add: username ALL=(ALL) NOPASSWD: ALL
```

* #### Firewall Config 

```
ufw enable
ufw allow 22,80,443,3000,996,7946,4789,2377/tcp; ufw allow 7946,4789,2377/udp;
```

* #### Set Host 

```
export USE_HOSTNAME=dog.example.com
Set up the server hostname
echo $USE_HOSTNAME > /etc/hostname
hostname -F /etc/hostname
```

* #### Configure Host File (/etc/hosts)

```
127.0.0.1       localhost
173.208.139.88  node0.tribestudios.io   node0
173.208.139.89  node1.tribestudios.io   node1
173.208.139.91  node2.tribestudios.io   node2
173.208.139.92  node3.tribestudios.io   node3
173.208.139.93  node4.tribestudios.io   node4
```

* #### Install Docker

```
curl -fsSL get.docker.com -o get-docker.sh

# Install Docker using the stable channel (instead of the default "edge")
CHANNEL=stable sh get-docker.sh

# Remove Docker install script
rm get-docker.sh
sudo usermod -aG docker aaron
```
