* connect to the openvpn of tryhackme
* start the labmachine and using the username and password given connect to ssh

```bash
ssh -o HostKeyAlgorithms=+ssh-rsa \
    -o PubkeyAcceptedAlgorithms=+ssh-rsa \
    username@labmachine-ip
```

* after exploiting any machine the first thing we have to do is 
```bash
whoami
```

* and check the host name of the machine
```bash
hostname
```

* and check the version of the kernel 
```bash
uname -a
```

* checking the services running in the machine
```bash
ps aux
```

* now the main part when we logged in as a user we have to check the sudo permissons of the user in that particular machine like what are the commands the user is allowed to perform
```bash
sudo -l
```

* now try to access the password file
```bash
cat /etc/shadow
```

* we can see the password of the root user and the user we logged in or anyother users present in HASHED format
* after that we have to check the connections made in the system

```bash
ip a && ifconfig
```

* to see anyother machines connected in the network we have to use `arp-scan`
* check which are the ports are in use

```bash
netstat -ano
```

* check the history of the commands used in the terminal
```bash 
history
```
