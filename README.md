# TCM-AcademyMachine



we found that FTP server is open in port 21, so we will try to connect to that FTP server using:
```bash
$ ftp <ip-address>

#with the following credentials 
#name: anonymous
#password: <anything> or anonymous
```

to retrive files:
```bash
$ get <file_name>
```
after we got the note.txt file from the ftp server it has the following:


la2eno kateb eno fe bel mawdoo3 safha w test page and because it is running a web server on port 80 we are going to use dirbuster to go through the directrories in the website, and after we used dirbuster we got the following results:

---


now we open those two pages 
- for the academy/index.php student regestration page and we will use the information we got from the note.txt file from the ftp server 
- for the admin/index.php we will use the credentials(admin, admin)

---

after we navigate to the student account we can see that we can upload a photo so we might abuse the upload functionality, and if it accept all file types we can upload a reverse shell php code.

---

so now we choose this code and put it in a file then upload it to the website

but don't forget to listen in your machine using "nc" command and edit the code to put your ip address so the victim connects to you.

---
now we got a connection to our machine

---
now because we are the www-get user and we are not the root we need some sort of privilage escalation so we will use linpeas.sh and download it in the victim machine and run it to see if it has some information that might help us

we ran a web server on our machine so the victim can download the linpeas through our machine

we will use wget to get the linpeas.sh!
now we are going to make it excutable and run it.

---
after we skimmed through the result of linpeas we found that there is a user grimmie that has a password "My_V3ryS3cur3_P4ss" so we used ssh to login into that machine with the credentials that we got using:
```bash
ssh grimmie@10.0.2.6
```

and we got a connection!


---
we can see that grimmie has a file called "backup.sh" and apparently there is a crojob made for this file to excute every minute and it seems that the root user created this cronjob which means every time it runs the script in this file it will run it with the privilage of the root user so we will try to modify the "backup.sh" file to add a script that give us a reverse shell and connect to our machine.

1. We add the reverse script

2. we listened on the port

3. WE BECAME ROOT!
---
