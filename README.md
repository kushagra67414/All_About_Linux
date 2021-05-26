# DevOps_Crunch

## Linux commands Everyone must know

1. whoami
2. who
3. hostname
4. uname -i
5. uptime
6. cal (calculator)
7. date

![image](https://user-images.githubusercontent.com/46487696/119563036-ac7c5080-bdc4-11eb-82f9-a0c397a20430.png)

![image](https://user-images.githubusercontent.com/46487696/119563086-c0c04d80-bdc4-11eb-8277-1d8c1cea631c.png)

![image](https://user-images.githubusercontent.com/46487696/119563106-cc137900-bdc4-11eb-924e-d322ce4839e0.png)

![image](https://user-images.githubusercontent.com/46487696/119563243-eea59200-bdc4-11eb-81de-554215054eb0.png)


## User and Group Management

Create user either by “adduser” or “useradd” <br>
Useradd simply creates the user while adduser are user-friendly they ask series of ques and create a primary group and add user to the group.Also create the home directory.<br>
In useradd we have to use flag “-d” to set the home directory. “–s” to add working shell <br>

Example => useradd kush1 –d /home/kush1  -s /bin/csh <br>

Lets create a user and set a password:

> Sudo useradd kush1 <br>
> Passwd kush1

Now, we have to provide the root privileges to the user i.e **kush1**.<br>
Redirect to the sudoers file to configure it<br>

**Either =>**

```
Sudo
Nano /etc/sudoers
```
**OR =>**

``` Sudo visudo ```

“visudo we will ensure that 1) no one else can modify the file at the same time, and 2) the file syntax is checked upon saving changes.” <br>

Command to add in sudoers file is:<br>

Kush1 ALL=(ALL) ALL

![image](https://user-images.githubusercontent.com/46487696/119564042-edc13000-bdc5-11eb-9325-e8c17d117f33.png)

Login to the new added user from root:

Command:
```
su kush1
Cd   /
ls
```

Here, we can see the host filesystem 

![image](https://user-images.githubusercontent.com/46487696/119564303-41cc1480-bdc6-11eb-9982-4c756c335f6a.png)

## User Management

Using usermod we can change the home directory to another existing one, edit the login shell, and an add an optional comment on the user (such as full name or employee information) as explained next.
	
Command:
> sudo usermod --home /Desktop/kush1 kush1 <br>
> sudo   usermod   --shell   /bin/sh   kush1 <br>
> by default home directory must be present  i.e /home/kush1. <br>

To see the changes

Command: 
> Cat /etc/passwd <br>

Here we can the info about user, password, home directory, shell and so on.

![image](https://user-images.githubusercontent.com/46487696/119564698-b30bc780-bdc6-11eb-824e-68d5a234a823.png)

usermod also allows you to lock (and unlock) an account and set its expiration date. To do so, use --lock (or -L), --unlock (or -U), and --expiredate (or -e), respectively. The expiration date must be specified using the YYYY-MM-DD format.

Command:

> sudo usermod  --lock kush1<br>
> su - kush1<br>
// will show an Authentication error

![image](https://user-images.githubusercontent.com/46487696/119564948-f6fecc80-bdc6-11eb-8720-6c2a40cc659f.png)

When an user is locked, an exclamation sign ! is placed before the encrypted password in /etc/shadow, thus disabling the account.

![image](https://user-images.githubusercontent.com/46487696/119565035-14339b00-bdc7-11eb-8b76-8cfeb02d0b91.png)


**chage:** change user password expiry information.

Command: <br>
> sudo chage -l kush1

![image](https://user-images.githubusercontent.com/46487696/119565326-74c2d800-bdc7-11eb-992d-c6789f8852d6.png)

> sudo chage --maxdays 60 kush1

Here, it means after 60 days we have to change the password of our machine.

**User delete:**

Command:

```> Userdel   kush2   -r```

the use of -r will ensure that all the user's files are removed as well.

To validate use command:

> Getent passwd| grep kush2
// Nothing will be shown at console

> Getent passwd| grep kush1
// Shows about the user kush1

![image](https://user-images.githubusercontent.com/46487696/119565524-ad62b180-bdc7-11eb-9036-8631b85ba11e.png)



## Group Management

Adding a group =>

![image](https://user-images.githubusercontent.com/46487696/119565916-2a8e2680-bdc8-11eb-8eca-7d9a2d4b0cba.png)

Fetching group details =>

![image](https://user-images.githubusercontent.com/46487696/119565952-35e15200-bdc8-11eb-9040-d90a4f2bdf43.png)



## Process Management in Linux

Kill command:

kill 2343  // kill the process of this particular process id
kill -9 2323,2564 // kill multiple process 

Process command:
![image](https://user-images.githubusercontent.com/46487696/119649781-a926aa80-be40-11eb-94d5-560514f0c41a.png)

ps -e | head -5

## grep| egrep | fgrep

grep "delhi" cities  // prints delhi from cities file

flag:
-i // ignore case sensitivity
-c //count number pattern repeat in file
-n // shows the line number of the pattern in file
-v // shows negation of pattern
-l //display file name if pattern matches from it 



**grep with regular expression:**

![image](https://user-images.githubusercontent.com/46487696/119623826-2e509600-be26-11eb-9d6b-258871bd1a41.png)

![image](https://user-images.githubusercontent.com/46487696/119634104-0403d600-be30-11eb-8fe6-b59f21a41268.png)

![image](https://user-images.githubusercontent.com/46487696/119634115-06fec680-be30-11eb-9b50-c54fd6afec92.png)

![image](https://user-images.githubusercontent.com/46487696/119634130-09f9b700-be30-11eb-877c-2fa23cb0ebdc.png)

