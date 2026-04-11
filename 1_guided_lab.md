# useing -p option when creating dirs does not give any errors
```
[ec2-user@ip-172-31-19-137 ~]$ mkdir -pv Music Pictures Videos
mkdir: created directory 'Music'
mkdir: created directory 'Pictures'
mkdir: created directory 'Videos'
[ec2-user@ip-172-31-19-137 ~]$ mkdir -pv Music Pictures Videos
[ec2-user@ip-172-31-19-137 ~]$ mkdir  Music Pictures Videos
mkdir: cannot create directory ‘Music’: File exists
mkdir: cannot create directory ‘Pictures’: File exists
mkdir: cannot create directory ‘Videos’: File exists
```
- without -p it give error
- -v is for verbose

# Create 6 files in each folder
```
[ec2-user@ip-172-31-19-137 ~]$ touch Music/song{1..6}.mp3
[ec2-user@ip-172-31-19-137 ~]$ touch Pictures/snap{1..6}.jpeg
[ec2-user@ip-172-31-19-137 ~]$ touch Videos/vid{1..6}.avi
[ec2-user@ip-172-31-19-137 ~]$ ls -R
.:
Music  Pictures  Videos  dir3  file1  file2

./Music:
song1.mp3  song2.mp3  song3.mp3  song4.mp3  song5.mp3  song6.mp3

./Pictures:
snap1.jpeg  snap2.jpeg  snap3.jpeg  snap4.jpeg  snap5.jpeg  snap6.jpeg

./Videos:
vid1.avi  vid2.avi  vid3.avi  vid4.avi  vid5.avi  vid6.avi

./dir3:
[ec2-user@ip-172-31-19-137 ~]$ ls -Rl
.:
total 0
drwxr-xr-x. 2 ec2-user ec2-user 108 Apr 11 04:50 Music
drwxr-xr-x. 2 ec2-user ec2-user 114 Apr 11 04:50 Pictures
drwxr-xr-x. 2 ec2-user ec2-user 102 Apr 11 04:50 Videos
drwxr-xr-x. 2 ec2-user ec2-user   6 Apr 11 04:38 dir3
-rw-r--r--. 1 ec2-user ec2-user   0 Apr 11 04:38 file1
-rw-r--r--. 1 ec2-user ec2-user   0 Apr 11 04:38 file2

./Music:
total 0
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 song1.mp3
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 song2.mp3
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 song3.mp3
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 song4.mp3
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 song5.mp3
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 song6.mp3

./Pictures:
total 0
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 snap1.jpeg
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 snap2.jpeg
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 snap3.jpeg
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 snap4.jpeg
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 snap5.jpeg
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 snap6.jpeg

./Videos:
total 0
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 vid1.avi
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 vid2.avi
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 vid3.avi
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 vid4.avi
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 vid5.avi
-rw-r--r--. 1 ec2-user ec2-user 0 Apr 11 04:50 vid6.avi

./dir3:
total 0
```


# Moving files
- mv song*.mp3 Music
- mv snap*.jpg Pictures
- mv fil*.avi Videos
- ls -r

# copy 1 and 2 file to family
```
[ec2-user@ip-172-31-19-137 family]$ cp ~/Music/song[12].mp3 ~/Pictures/snap[12].jpeg ~/Videos/vid[12].avi .
[ec2-user@ip-172-31-19-137 family]$ ls
snap1.jpeg  snap2.jpeg  song1.mp3  song2.mp3  vid1.avi  vid2.avi
[ec2-user@ip-172-31-19-137 family]$
```

# cp[y 3 and 4 to friends

# copy friends and family into work folder

```
[ec2-user@ip-172-31-19-137 family]$ cp ~/Music/song[12].mp3 ~/Pictures/snap[12].jpeg ~/Videos/vid[12].avi .
[ec2-user@ip-172-31-19-137 family]$ ls
snap1.jpeg  snap2.jpeg  song1.mp3  song2.mp3  vid1.avi  vid2.avi
[ec2-user@ip-172-31-19-137 family]$ cd ../friends/
[ec2-user@ip-172-31-19-137 friends]$ cp ~/Music/song[34].mp3 ~/Pictures/snap[34].jpeg ~/Videos/vid[34].avi .
[ec2-user@ip-172-31-19-137 friends]$ ls
snap3.jpeg  snap4.jpeg  song3.mp3  song4.mp3  vid3.avi  vid4.avi
[ec2-user@ip-172-31-19-137 friends]$ cd ../work/
[ec2-user@ip-172-31-19-137 work]$ cp -r ../friends/ ../family/
```

# use treee
