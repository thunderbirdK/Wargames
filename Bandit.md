#Wargames
##bandit
### Level - 0 ###
Connect to the bandit using SSH to the bandit server using putty -  bandit.labs.overthewire.org. Username - bandit0 Password -  bandit0

### Level - 1 ###
SSH was successful and with the ls command found the readme file.here is a readme file in bandit 0’s home directory. We can get the password with.
with VI editor can get the hash code. "boJ9jbbUNNfktd78OOpsqOltutMc3MY1"

### Level - 2 ###
SSH using bandit1@bandit.labs.overthewire.org
a file on the desktop named ‘-‘. Since the dash in bash is a special character cat ./-
and use the same password: boJ9jbbUNNfktd78OOpsqOltutMc3MY1</n>
password for the next level:CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

### Level - 3 ###
SSH using bandit2@bandit.labs.overthewire.org</n>
we see that there is a file with spaces in the name. accomplished this by typing cat spaces\ in\ this\ filename 
and use the same password:CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9</n>
password for the next level:UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

### Level - 4 ###
SSH using bandit3@bandit.labs.overthewire.org</n>
There is a folder called inhere, that appears blank at the first glance. However, typing $ ls -la shows that there is a hidden file called .hidden containing the key
cd inhere
ls -a
cat .hidden
and use the same password:UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK</n>
password fort the next level :pIwrPrtPN36QITSp3EQaw936yaFoFgAB

### Level - 5 ###
SSH using bandit4@bandit.labs.overthewire.org
Here we have a folder called inhere, and a few files inside. The page says the password is in the only human readable file, so with the file command we can see that -file07 is the only file with ASCII text.
cat ./-file07
and use the same password:pIwrPrtPN36QITSp3EQaw936yaFoFgAB
password for the next level: koReBOKuIDDepwhWk7jZC0RTdopnAYKh

### Level - 6 ###
SSH using bandit5@bandit.labs.overthewire.org
They told us the file containing the password is 1033 bytes, so we can use the find command to find a file of a specific size.
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
and use the same password: koReBOKuIDDepwhWk7jZC0RTdopnAYKh
password for the next level:DXjZPULLxYr17uwoI01bNLQbtFemEgo7

### Level - 7 ###
SSH using bandit6@bandit.labs.overthewire.org
There is a file called data.txt in the home directory. It is a 
and use the same password:DXjZPULLxYr17uwoI01bNLQbtFemEgo7
password for the next level: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

### Level - 8 ###
SSH using bandit7@bandit.labs.overthewire.org
huge file that we need to parse through. The password is located next to the word millionth, so 
cat data.txt | grep millionth
and use the same password:HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
password for the next level:cvX2JJa4CFALtqS87jk27qwqGhBM9plV

### Level - 9 ###
SSH using bandit8@bandit.labs.overthewire.org
The password is found on the only unique line in the file data.txt
sort data.txt | uniq -u
and use the same password: cvX2JJa4CFALtqS87jk27qwqGhBM9plV
password for the next level:UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

### Level - 10 ###
SSH using bandit9@bandit.labs.overthewire.org
the file data.txt is a binary file this time. We can’t easily grep through it
strings data.txt | grep =
and use the same password: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
password for the next level:truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

### Level - 11 ###
SSH using bandit10@bandit.labs.overthewire.org
The password is encoded with base64 
base64 -d -i data.txt
and use the same password:truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
password for the next level: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

### Level - 12 ###
SSH using bandit11@bandit.labs.overthewire.org
text has been rotated 13 letters
cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
and use the same password:IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
password for the next level: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

### Level - 13 ###
SSH using bandit12@bandit.labs.overthewire.org
hexdump of a file that has been repeatedly compressed
bandit12@melinda:~$ mkdir /tmp/zer0w1re
bandit12@melinda:~$ cd /tmp/zer0w1re
bandit12@melinda:/tmp/zer0w1re$ cat ~/data.txt | xxd -r > ./data
bandit12@melinda:/tmp/zer0w1re$ file data 
data: gzip compressed data, was "data2.bin", from Unix, last modified: Thu Jun  6 13:59:44 2013, max compression
bandit12@melinda:/tmp/zer0w1re$ mv data{,.gz}
bandit12@melinda:/tmp/zer0w1re$ gunzip data.gz 
bandit12@melinda:/tmp/zer0w1re$ file data 
data: bzip2 compressed data, block size = 900k
bandit12@melinda:/tmp/zer0w1re$ mv data{,.bz2}
bandit12@melinda:/tmp/zer0w1re$ bzip2 -d data.bz2 
bandit12@melinda:/tmp/zer0w1re$ file data 
data: gzip compressed data, was "data4.bin", from Unix, last modified: Thu Jun  6 13:59:43 2013, max compression
bandit12@melinda:/tmp/zer0w1re$ mv data{,.gz}
bandit12@melinda:/tmp/zer0w1re$ gunzip data.gz 
bandit12@melinda:/tmp/zer0w1re$ file data 
data: POSIX tar archive (GNU)
bandit12@melinda:/tmp/zer0w1re$ tar xvf data 
data5.bin
bandit12@melinda:/tmp/zer0w1re$ file data5.bin 
data5.bin: POSIX tar archive (GNU)
bandit12@melinda:/tmp/zer0w1re$ tar xvf data5.bin 
data6.bin
bandit12@melinda:/tmp/zer0w1re$ file data6.bin 
data6.bin: bzip2 compressed data, block size = 900k
bandit12@melinda:/tmp/zer0w1re$ mv data6{.bin,.bz2}
bandit12@melinda:/tmp/zer0w1re$ bzip2 -d data6.bz2 
bandit12@melinda:/tmp/zer0w1re$ ls
data5.bin  data6
bandit12@melinda:/tmp/zer0w1re$ file data6
data6: POSIX tar archive (GNU)
bandit12@melinda:/tmp/zer0w1re$ tar xvf data6 
data8.bin
bandit12@melinda:/tmp/zer0w1re$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", from Unix, last modified: Thu Jun  6 13:59:43 2013, max compression
bandit12@melinda:/tmp/zer0w1re$ mv data8{.bin,.gz} 
bandit12@melinda:/tmp/zer0w1re$ mv data8{.bin,.gz} 
bandit12@melinda:/tmp/zer0w1re$ ls
data5.bin  data6  data8
bandit12@melinda:/tmp/zer0w1re$ file data8
data8: ASCII text
bandit12@melinda:/tmp/zer0w1re$ cat data8 
and use the same password: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
password for the next level:8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

### Level - 14 ###

SSH using bandit13@bandit.labs.overthewire.org
and use the same password:8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
Password for the next level: 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e

bandit13@melissa:~$ ls
sshkey.private
bandit13@melissa:~$ ssh -i sshkey.private bandit14@localhost
Could not create directory '/home/bandit13/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 9d:09:d9:46:84:df:f9:dd:cc:7c:dc:49:a0:95:b2:10.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit13/.ssh/known_hosts).
bandit14@melissa:~$ cat /etc/bandit_pass/bandit14

### Level - 15 ###
the password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost
BfMYroe26WYalil77FoDi9qh59eK5xNr

bandit14@melissa:~$ telnet localhost 30000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
 
Connection closed by foreign host.

### Level - 16 ###

SSH using bandit15@bandit.labs.overthewire.org
Using password: BfMYroe26WYalil77FoDi9qh59eK5xNr

echo `cat /etc/bandit_pass/bandit15` | openssl s_client -connect localhost:30001

echo `cat /etc/bandit_pass/bandit15` | openssl s_client -connect localhost:30001 -quiet
depth=0 CN = localhost

Next level password:cluFn7wTiGryunymYOu4RcffSxQluehd

### Level - 17 ###

SSH using bandit16@bandit.labs.overthewire.org
using password cluFn7wTiGryunymYOu4RcffSxQluehd

nmap -p31000-32000 localhost -sV run this to get the SSH port
echo `cat /etc/bandit_pass/bandit16` | openssl s_client -connect localhost:31518 -quiet
depth=0 CN = localhost
then
echo `cat /etc/bandit_pass/bandit16` | openssl s_client -connect localhost:31790 -quiet
depth=0 CN = localhost
RSA KEY:
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=


### Level - 18 ###

Using the RSA key found we can SSH to the next level. 
Use the diff key n this level.
bandit17@melissa:~$ ls
passwords.new  passwords.old
bandit17@melissa:~$ diff passwords.new  passwords.old
42c42
kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
bECYSoXjOeGseirUCztuCBDF3xXqE7By

Password we need is : kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

### Level - 19 ###

SSH using bandit18@bandit.labs.overthewire.org
Password : kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

but when we login system log us out,

so here what we can do SSH using following command.
bandit18@bandit.labs.overthewire.org -t 'command; cat readme'

Password to the next level is :IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x

### Level - 20 ###

SSH using bandit19@bandit.labs.overthewire.org
Password: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x

Not sure what it does so we can run it and see the usage.

bandit19@melinda:~$ ls
bandit20-do

bandit19@melinda:~$ ./bandit20-do 0
env: 0: No such file or directory
bandit19@melinda:~$ ./bandit20-do cat  




^C
bandit19@melinda:~$ ./bandit20-do cat /etc/bandit_pass/bandit2
cat: /etc/bandit_pass/bandit2: Permission denied
bandit19@melinda:~$ ./bandit20-do cat /etc/bandit_pass/bandit20

### Level - 21 ###

SSH using bandit20@bandit.labs.overthewire.org
Password: GbKksEFF4yrVs6il55v6gwY5aVje5f0j

We login and there is a file ‘suconnect’. It makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level . If the password is correct, it will transmit the password for the next level 

bandit20@melinda:~$ nc -l 12345 (window 1)
bandit20@melinda:~$ ./suconnect 12345 (window 2)
bandit20@melinda:~$ nc -l 12345
GbKksEFF4yrVs6il55v6gwY5aVje5f0j(window1)

next password: gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr

### Level - 22 ###

SSH using bandit21@bandit.labs.overthewire.org
Password: gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr

we need to look at. In /etc/cron.d there are a bunch of files

bandit21@melissa:~$ cd /etc/cron.d/
bandit21@melissa:/etc/cron.d$ ls -la
total 100
drwxr-xr-x  2 root root 4096 2013-01-03 16:39 .
drwxr-xr-x 94 root root 4096 2013-03-18 15:53 ..
-rw-r--r--  1 root root   54 2013-01-03 16:39 boobiesbot-check
-rw-r--r--  1 root root   61 2012-07-05 09:34 cronjob_bandit22
-rw-r--r--  1 root root   61 2012-07-05 09:34 cronjob_bandit23
-rw-r--r--  1 root root   61 2012-07-05 09:35 cronjob_bandit24
-rw-r--r--  1 root root   35 2012-03-29 14:16 eloi0
-rw-r--r--  1 root root   35 2012-04-07 18:33 eloi1
-rw-r--r--  1 root root   51 2012-12-23 00:06 hintbot-check
-rw-------  1 root root  233 2012-09-14 13:16 manpage3_resetpw_job
-rw-r--r--  1 root root  506 2012-06-19 03:06 php5
-rw-r--r--  1 root root  102 2011-01-05 11:23 .placeholder
-rw-r--r--  1 root root   58 2011-11-13 23:08 semtex0-32
-rw-r--r--  1 root root   58 2011-11-13 23:08 semtex0-64
-rw-r--r--  1 root root   59 2011-11-13 23:08 semtex0-ppc
-rw-r--r--  1 root root   36 2011-11-25 14:00 semtex10
-rw-r--r--  1 root root  143 2011-11-13 23:08 semtex12
-rw-r--r--  1 root root   35 2011-11-13 23:08 semtex5
-rw-r--r--  1 root root   29 2011-11-13 23:08 semtex6
-rw-r--r--  1 root root   96 2011-11-25 14:00 semtex8
-rw-r--r--  1 root root  134 2011-11-13 23:14 semtex9
-rw-r--r--  1 root root   29 2011-11-13 23:07 vortex0
-rw-r--r--  1 root root   30 2012-03-24 21:00 vortex20
-rw-r--r--  1 root root   52 2012-12-23 00:06 vulnbot0-check
-rw-r--r--  1 root root   52 2012-12-23 00:06 vulnbot1-check
bandit21@melissa:/etc/cron.d$ cat cronjob_bandit22
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@melissa:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@melissa:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI

next password: Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI


### Level - 23 ###

SSH using bandit22@bandit.labs.overthewire.org
Password: Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI

bandit22@melissa:~$ cd /etc/cron.d
bandit22@melissa:/etc/cron.d$ ls
boobiesbot-check  eloi1                 semtex0-64   semtex6   vulnbot0-check
cronjob_bandit22  hintbot-check         semtex0-ppc  semtex8   vulnbot1-check
cronjob_bandit23  manpage3_resetpw_job  semtex10     semtex9
cronjob_bandit24  php5                  semtex12     vortex0
eloi0             semtex0-32            semtex5      vortex20
bandit22@melissa:/etc/cron.d$ cat cronjob_bandit23
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh &> /dev/null
bandit22@melissa:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh
!/bin/bash
 
myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
 
echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
 
cat /etc/bandit_pass/$myname > /tmp/$mytarget
 
Run the script:
bandit22@melissa:/etc/cron.d$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
 
Check contents of that file in /tmp:
bandit22@melissa:/etc/cron.d$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n

next password: jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n

### Level - 24 ###

SSH using bandit23@bandit.labs.overthewire.org 
Password: jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n

bandit23@melissa:~$ cd /etc/cron.d
bandit23@melissa:/etc/cron.d$ ls
boobiesbot-check  eloi1                 semtex0-64   semtex6   vulnbot0-check
cronjob_bandit22  hintbot-check         semtex0-ppc  semtex8   vulnbot1-check
cronjob_bandit23  manpage3_resetpw_job  semtex10     semtex9
cronjob_bandit24  php5                  semtex12     vortex0
eloi0             semtex0-32            semtex5      vortex20
bandit23@melissa:/etc/cron.d$ cat cronjob_bandit24
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@melissa:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
!/bin/bash
 
myname=$(whoami)
 
cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in *;
do
echo "Handling $i"
./$i
rm -f $i
done
 
Let's begin the process to create our script:
bandit23@melissa:/etc/cron.d$ mkdir /tmp/cccc
bandit23@melissa:/etc/cron.d$ cd /tmp/cccc
bandit23@melissa:/tmp/cccc$ vi dump.sh
     !/bin/bash
     ls -la >> /tmp/cccc/list.txt
 
chmod 777 is probably overkill, this stuff gets erased.
bandit23@melissa:/tmp/cccc$ chmod 777 dump.sh
bandit23@melissa:/tmp/cccc$ chmod -R 777 /tmp/cccc
bandit23@melissa:/tmp/cccc$ cp dump.sh /var/spool/bandit24/
 
Wait one minute for the cronjob to run then check our list.txt file:
bandit23@melissa:/tmp/cccc$ cat list.txt
total 100
drwxr-xr-x  2 root root 4096 2013-01-03 16:39 .
drwxr-xr-x 94 root root 4096 2013-03-18 15:53 ..
-rw-r--r--  1 root root   54 2013-01-03 16:39 boobiesbot-check
-rw-r--r--  1 root root   61 2012-07-05 09:34 cronjob_bandit22
-rw-r--r--  1 root root   61 2012-07-05 09:34 cronjob_bandit23
-rw-r--r--  1 root root   61 2012-07-05 09:35 cronjob_bandit24
-rw-r--r--  1 root root   35 2012-03-29 14:16 eloi0
-rw-r--r--  1 root root   35 2012-04-07 18:33 eloi1
-rw-r--r--  1 root root   51 2012-12-23 00:06 hintbot-check
-rw-------  1 root root  233 2012-09-14 13:16 manpage3_resetpw_job
-rw-r--r--  1 root root  506 2012-06-19 03:06 php5
-rw-r--r--  1 root root  102 2011-01-05 11:23 .placeholder
-rw-r--r--  1 root root   58 2011-11-13 23:08 semtex0-32
-rw-r--r--  1 root root   58 2011-11-13 23:08 semtex0-64
-rw-r--r--  1 root root   59 2011-11-13 23:08 semtex0-ppc
-rw-r--r--  1 root root   36 2011-11-25 14:00 semtex10
-rw-r--r--  1 root root  143 2011-11-13 23:08 semtex12
-rw-r--r--  1 root root   35 2011-11-13 23:08 semtex5
-rw-r--r--  1 root root   29 2011-11-13 23:08 semtex6
-rw-r--r--  1 root root   96 2011-11-25 14:00 semtex8
-rw-r--r--  1 root root  134 2011-11-13 23:14 semtex9
-rw-r--r--  1 root root   29 2011-11-13 23:07 vortex0
-rw-r--r--  1 root root   30 2012-03-24 21:00 vortex20
-rw-r--r--  1 root root   52 2012-12-23 00:06 vulnbot0-check
-rw-r--r--  1 root root   52 2012-12-23 00:06 vulnbot1-check
total 93
drwx-wx--- 13 bandit24 bandit23  1024 2013-03-21 02:44 .
drwxr-xr-x  6 root     root      4096 2012-07-05 09:24 ..
-rw-r--r--  1 bandit23 bandit23   130 2012-10-30 20:50 .aaa.sh
drwxr-xr-x  2 bandit23 bandit23  1024 2013-01-21 03:15 asdsd
-rw-------  1 bandit23 bandit23 12288 2012-06-05 15:22 .a.sh.swo
drwxr-xr-x  2 bandit23 bandit23  1024 2013-02-25 11:35 bandit23
drwxrwxrwx  2 bandit23 bandit23  1024 2013-03-11 20:15 bandit24
-rw-------  1 bandit23 bandit23 12288 2012-10-14 17:23 .catpass.sh.swp
-rwxr-xr-x  1 bandit23 bandit23    42 2013-03-21 02:44 dump.sh
drwxr-xr-x  2 bandit23 bandit23  1024 2012-12-20 18:31 galo
-rw-------  1 bandit23 bandit23 12288 2012-11-14 04:45 .getpass.swp
drwxrwxrwx  2 bandit23 bandit23  1024 2013-03-13 22:07 inhere
drwxr-xr-x  2 bandit23 bandit23  1024 2012-07-06 13:26 lolwut
drwx------  2 root     root     12288 2012-05-30 14:18 lost+found
drwxr-xr-x  2 bandit23 bandit23  1024 2013-02-23 21:44 pass
drwxr-xr-x  2 bandit24 bandit24  1024 2012-12-30 12:44 passjurgen
-rw-r--r--  1 bandit24 bandit24    33 2012-10-13 09:33 .plop
-rw-------  1 bandit23 bandit23 12288 2013-01-23 19:13 .shellcode.swo
-rw-------  1 bandit23 bandit23 12288 2013-01-23 19:03 .shellcode.swp
drwxr-xr-x  2 bandit23 bandit23  1024 2012-09-28 14:24 sub
-rw-r--r--  1 bandit23 bandit23     3 2012-09-28 14:38 .t1
-rw-r--r--  1 bandit23 bandit23     3 2012-09-28 14:38 .t2
-rw-r--r--  1 bandit23 bandit23     3 2012-09-28 14:38 .t3
drwxr-xr-x  2 bandit23 bandit23  1024 2012-11-27 17:46 zdenial
 
Nice, we see some interesting files, lets' go to this one:
bandit23@melissa:/tmp/cccc$ cd  /var/spool/bandit24/pass
bandit23@melissa:/var/spool/bandit24/pass$ ls
pass
bandit23@melissa:/var/spool/bandit24/pass$ cat pass
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ

Next password: UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ

### Level - 25 ###

SSH using bandit24@bandit.labs.overthewire.org
Password: UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ

They say that pin we have to enter the correct pin code to get the password and its a 4 digit one.we cannot enter all 1000 to 9999 combinations by hand. what we can use a script or a loop.

for i in $(seq -f "%04g" 1000 9999); do echo 'UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ '${i} | nc localhost 30002; done

password is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG


### Level - 65 ###


SSH using bandit25@bandit.labs.overthewire.org
Password: uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG

once we logged in it will close the connection
what u can do is bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext

then cat /usr/bin/showtext

then ssh -i ~/ bandit26@localhost again. This time I got the pause at "More". I pressed "v" and was presented with a vi interface. I then typed :r /etc/bandit_pass/bandit26

password  5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z