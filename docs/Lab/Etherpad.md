# Etherpad
!!! quote
    Etherpad is a highly customizable open source online editor providing collaborative editing in really real-time.

## Installing Etherpad on Ubuntu 24.04

!!! warning
    I got partway through this process and then got pulled onto something else. 

    TODO: Actually finish installing Etherpad, and get it up and running. Look into running it via Docker?

Make an `A` record pointing to the server IP address.

### Install Node.js
From [NodeSource Installation Instructions (DEB)](https://github.com/nodesource/distributions?tab=readme-ov-file#using-ubuntu-nodejs-22)
```
sudo apt-get install -y curl
curl -fsSL https://deb.nodesource.com/setup_22.x -o nodesource_setup.sh
sudo -E bash nodesource_setup.sh
sudo apt-get install -y nodejs
node -v
```

### Make a dedicated Etherpad user
From [How To Install the Etherpad Collaborative Web Editor on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-the-etherpad-collaborative-web-editor-on-ubuntu-20-04)
```
sudo adduser --system --group --home /opt/etherpad etherpad
passwd etherpad
usermod -aG sudo etherpad
sudo -u etherpad bash
cd /opt/etherpad
```

