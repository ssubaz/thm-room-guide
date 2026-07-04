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
