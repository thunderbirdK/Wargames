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