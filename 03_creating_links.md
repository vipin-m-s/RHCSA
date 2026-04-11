# creating links
- process - pid
- user - user id
- group - group id
- file - inode/index node
  - they contain the metadata about files and the link to data blocks
  - inode - permission - links - user - group - size - time - name
- Link
  - It is a link to the inode
  - We can give different name to the samer file

```
[ec2-user@ip-172-31-19-137 tesst]$ ls -li
total 0
438657 -rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 05:14 file1

[ec2-user@ip-172-31-19-137 tesst]$ ln file1 file3

[ec2-user@ip-172-31-19-137 tesst]$ ls -li
total 0
438657 -rw-r--r--. 2 ec2-user ec2-user 0 Apr 11 05:14 file1
438657 -rw-r--r--. 2 ec2-user ec2-user 0 Apr 11 05:14 file3
```

File allocation table  - mapping between the inode and file path
- 102 ---> /root/file1
- 103 ---> /root/file4
- 102 ----> /root/file2


- Thesee are what we call hard links
- They have limitations
- We cannot create hard link from different file system ( inode is specific to file system and hard links work on inode ) 
- It can be used only with regular files 
<img width="620" height="513" alt="Screenshot 2026-04-11 at 10 59 06 AM" src="https://github.com/user-attachments/assets/43198b60-574f-45ea-b9c5-8abf935bfe3b" />

# Symlink or symbolic links
- It allows us to create links between file sstem and and also links to folders

## use case 1 : WHen the files are in very complex folder structure
```
[ec2-user@ip-172-31-19-137 test2]$ touch /usr/share/vips/test/new/html/index.html
```

```
[ec2-user@ip-172-31-19-137 test2]$ ln -s /usr/share/vips/test/new/html/ ~ec2-user
lrwxrwxrwx. 1 ec2-user ec2-user  30 Apr 11 05:37 html -> /usr/share/vips/test/new/html/
```
It will also create a different inode number
```
 1216317 lrwxrwxrwx. 1 ec2-user ec2-user  30 Apr 11 05:37 html -> /usr/share/vips/test/new/html/

[ec2-user@ip-172-31-19-137 html]$ ls -li /usr/share/vips/test/new/
total 0
438676 drwxr-xr-x. 2 root root 24 Apr 11 05:36 html
```
Easy access to complex dir structure
```
[ec2-user@ip-172-31-19-137 ~]$ cd html
[ec2-user@ip-172-31-19-137 html]$ ls
index.html
[ec2-user@ip-172-31-19-137 html]$
```

## Use case 2:- We can create symlink to files which are regularly accessed. Logs etc
```
[ec2-user@ip-172-31-19-137 ~]$ ln -s /usr/share/vips/test/new/html/index.html .

lrwxrwxrwx. 1 ec2-user ec2-user  40 Apr 11 05:40 index.html -> /usr/share/vips/test/new/html/index.html
```

# we can go to the original folder to where the link is pointing to using -p option
```
[ec2-user@ip-172-31-19-137 ~]$ cd -P html
[ec2-user@ip-172-31-19-137 html]$ pwd
/usr/share/vips/test/new/html
[ec2-user@ip-172-31-19-137 html]$
```


