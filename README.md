# Basic-Linux-Commands
assignment on basic linux commands

---
1. Create a user with user group.
```
sudo useradd raisa
id raisa
sudo passwd raisa
```
2. Create two directories in user's home directory named os-concepts and ubuntu-is-the-best.
```
sudo mkdir /home/raisa
sudo chown raisa:raisa /home/raisa
sudo chmod 700 /home/raisa
su raisa
cd ~
pwd
mkdir os-concepts
mkdir ubuntu-is-the-best
```
3. Create two files on each directory.
```
cd os-concepts
touch file1.txt file2.txt
cd ..
cd ubuntu-is-the-best
touch file1.txt file2.txt
```
4. List the files with detailed information ( including file permission ).
```
ls -l
```
5.  Update file permission so that owner can read,write and group can only read and others can not do anything.
```
chmod 640 file1.txt file2.txt
```
6. Create another group.
```
su raisavbox
cd ~
sudo groupadd second_group
```
7. Update file ownership to the newly created group.
```
sudo chown :second_group /home/raisa/os-concepts/file1.txt
sudo chown :second_group /home/raisa/os-concepts/file2.txt
sudo chown :second_group /home/raisa/ubuntu-is-the-best/file1.txt
sudo chown :second_group /home/raisa/ubuntu-is-the-best/file2.txt
```
8. Add the user to the new group.
```
sudo usermod -aG second_group raisa
getent group second_group 
```
9. Create a file called crash.in ( File should contain the word crash in it ) in different directories and then find the file in all the locations using find command.
```
vim crash.in
mkdir test_dir
cd test_dir
vim crash.in
cd ..
su raisa
cd ~
cd ubuntu-is-the-best
vim crash.in
sudo find / -type f -name "crash.in"
```
10. Then, replace the lines with crash to broken to all files ( use sed, xargs ).
```
sudo find / -type f -name "crash.in" -exec sed -i 's/crash/broken/g' {} +
```
