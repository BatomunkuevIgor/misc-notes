How to use an ISO file as offline repository in Debian
1. Create the folders (mountpoint) to mount the ISO files
</br>
sudo mkdir -p /media/repo_1</br>
sudo mkdir -p /media/repo_2</br>
sudo mkdir -p /media/repo_3</br>

2. mount the ISO files
</br>
sudo mount -o loop /home/$USER/Downloads/debian-8.0.0-amd64-DVD-1.iso /media/repo_1/</br>
sudo mount -o loop /home/$USER/Downloads/debian-8.0.0-amd64-DVD-2.iso /media/repo_2/</br>
sudo mount -o loop /home/$USER/Downloads/debian-8.0.0-amd64-DVD-3.iso /media/repo_3/</br>

3. edit the /etc/apt/sources.list file to add the repository

edit the /etc/apt/sources.list file with text editor of your choice, like gedit or nano and add those lines bellow.</br>
deb file:///media/repo_1/  jessie main contrib</br>
deb file:///media/repo_2/  jessie main contrib</br>
deb file:///media/repo_3/  jessie main contrib</br>
