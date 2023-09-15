# how-to-host-website-using-apache-and-s3-bucker
```
apt update -y
```
```
apt install apache2 -y
```
Download Source code 
```
cd /home/ubuntu
wget https://www.free-css.com/assets/files/free-css-templates/download/page296/klinik.zip
apt install zip -y
unzip   klinik.zip
cd clinic-website-template/
rm -rf img # upload img folder in s3
mv * /var/www/html/
```
Install and Configure s3fs
```
sudo apt-get install s3fs -y 
 
```
Next, you'll need to configure s3fs with your AWS S3 credentials. You can do this by editing the /etc/passwd-s3fs file or by creating a .passwd-s3fs file in your home directory with the following forma
```
vim /etc/passwd-s3fs
ACCESS_KEY:SECRET_KEY
sudo chmod 600 /etc/passwd-s3fs


```


Mount the S3 Bucket:
```
mkdir -p /home/ubuntu/s3
sudo s3fs BUCKET_NAME /home/ubuntu/s3 -o allow_other
df -h

```
df -h result output 
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       7.6G  1.8G  5.8G  24% /
tmpfs           483M     0  483M   0% /dev/shm
tmpfs           194M  844K  193M   1% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/xvda15     105M  6.1M   99M   6% /boot/efi
tmpfs            97M  4.0K   97M   1% /run/user/1000
s3fs             16E     0   16E   0% /home/ubuntu/s3
#Configure Apache:
