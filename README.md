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
