# Parallels 17 Kali Linux 
A guide on installing Kali Linux on Apple arm chips using Parallels 17, including a troubleshoot for ‘Parallels Tools’ installation.

## Dependencies 
### Host machine
kali-linux-2021.2-installer-arm64.iso - [kali-images](https://old.kali.org/kali-images/kali-2021.2/)
```
wget https://old.kali.org/kali-images/kali-2021.2/kali-linux-2021.2-installer-arm64.iso
```
### VM guest
linux-kbuild-5.10_5.10.28-1kali1_arm64.deb - [Download](http://old.kali.org/kali/pool/main/l/linux/)
```
wget http://old.kali.org/kali/pool/main/l/linux/linux-kbuild-5.10_5.10.28-1kali1_arm64.deb
```
linux-headers-5.10.0-kali7-common_5.10.28-1kali1_all.deb - [Download](http://old.kali.org/kali/pool/main/l/linux/)
```
wget http://old.kali.org/kali/pool/main/l/linux/linux-headers-5.10.0-kali7-common_5.10.28-1kali1_all.deb
```
linux-headers-5.10.0-kali7-arm64_5.10.28-1kali1_arm64.deb - [Download](http://old.kali.org/kali/pool/main/l/linux/)
```
wget http://old.kali.org/kali/pool/main/l/linux/linux-headers-5.10.0-kali7-arm64_5.10.28-1kali1_arm64.deb
```

## Process
1. Stranded VM install using the iso file
2. Fix apt-get update issue [Ref](https://superuser.com/questions/1644520/apt-get-update-issue-in-kali)
```
wget -q -O - https://archive.kali.org/archive-key.asc | sudo gpg --dearmor -o /usr/share/keyrings/kali-archive-keyring.gpg
```
3. Install dkms and libelf-dev
```
sudo apt update 
sudo apt install dkms 
sudo apt install libelf-dev
```
4. Install Linux headers [Ref](https://forum.parallels.com/threads/kali-linux-2022-2-parallels-tools-installation.357691/)
```
sudo dpkg -i linux-headers-5.10.0-kali7-arm64_5.10.28-1kali1_arm64.deb
sudo dpkg -i linux-kbuild-5.10_5.10.28-1kali1_arm64.deb
sudo dpkg -i linux-headers-5.10.0-kali7-common_5.10.28-1kali1_all.deb
```
5. Install Parallels Tools
Menu bar > Actions > Install Parallels Tools
```
sudo mount -oro,exec,remount /media/cdrom0
sudo /media/cdrom0/install
```