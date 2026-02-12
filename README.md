# falinks-metadata

This repo contains metadata and all the details of the 15 inch UAV equipped with Nvidia Orin Nano. A QR code on the UAV will link to indivudual pages for each UAV, containing its specifications, username, passwords, IP addresses, and other relevant information. 

Please make sure that all of the data in the individual UAV pages is kept up to date and accurate.

## Structure
- Each UAV has its own markdown file named after its unique identifier (e.g., `falinks-01.md`).
- Each file contains sections for specifications, network details, and other relevant information at the top.
- For history and any changes to the UAVs, a section of "Change Log" is included at the bottom of each file. Please mantain this changelog for each UAV.

## Hostname
To change the hostname from dexter to falinks0x follow the following steps, where x is the number of the quadrotor:

  1. `sudo hostnamectl set-hostname falinks0x`
  2. `sudo vim /etc/hosts` and replace the old hostname with the new one in the line starting with `127.0.1.1`.
  3. Verify the change: `hostnamectl`
  4. Restart the system to apply changes completely: `sudo reboot`

## Username change
Since we don't want anything to do with dexter name, changing the username from dexter to falinks, by creating a new falinks user, and adding it to the same groups as the dexter user. NOTE: check if any other permissions are to be given to the falinks user. 

The steps are as follows:
  1. Create a new user: `sudo adduser falinks`
  2. Add the new user to the same groups as dexter: `sudo usermod -aG sudo,adm,dialout,cdrom,floppy,plugdev,lpadmin,sambashare`
  3. Reboot, `sudo reboot`
  4. Login with the `falinks` user and setup the autologin procedure. 
  5. Goto `/etc/gdm3/custom.conf` and change the line `AutomaticLoginEnable = true` to `AutomaticLoginEnable = true` and `AutomaticLogin = falinks`.
  6. Reboot again to apply the changes: `sudo reboot`

## Install `jtop`

If jtop says that jetpack is missing. Installing via `sudo apt install nvidia-jetpack`. NOTE: OpenCV is not showing CUDA compilation. check if that is the case or not. If not install OpenCV with CUDA support and see if jtop can detect it. 

## Install Docker

1. Install Docker only via the convienence script. any other way installs the ugly version of docker aka the Docker Desktop.
The commands are :
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
```

2. Follow the post install steps to make sure that docker works on non-root user. Although this is not needed, its good to use docker without sudo. The post innstall scripts are provided here for convienence. This will enable the docker service to start on boot as well.

```
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```

