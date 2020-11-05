##How to use an ISO file as offline repository in Debian

### Create the folders (mountpoint) to mount the ISO files
```
sudo mkdir -p /media/repo_1
sudo mkdir -p /media/repo_2
sudo mkdir -p /media/repo_3
```
### mount the ISO files
```
sudo mount -o loop /home/$USER/Downloads/debian-8.0.0-amd64-DVD-1.iso /media/repo_1/
sudo mount -o loop /home/$USER/Downloads/debian-8.0.0-amd64-DVD-2.iso /media/repo_2/
sudo mount -o loop /home/$USER/Downloads/debian-8.0.0-amd64-DVD-3.iso /media/repo_3/
```
### edit the /etc/apt/sources.list file to add the repository
```
deb file:///media/repo_1/ jessie main contrib
deb file:///media/repo_2/ jessie main contrib
deb file:///media/repo_3/ jessie main contrib
```
