# Ubuntu-16.04-Setup

## References
* https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04#option-2-manually-install-the-key
* https://www.ostechnix.com/build-packages-source-using-checkinstall/
* https://scribles.net/installing-software-from-source-code-with-checkinstall/
* https://askubuntu.com/a/533636/708443

## First commands as new user:
```bash
sudo apt-get update
sudo apt-get upgrade
mkdir bin
mkdir src
mkdir scripts

# Build some common software
sudo apt-get install default-jre autoconf build-essential git checkinstall

# LMOD Installation
sudo apt-get install lmod environment-modules
# After this use this link as a reference  https://askubuntu.com/a/533636/708443

# Any python installation (3.7 for this example)
sudo apt-get build-dep python3.5

cd src
wget https://www.python.org/ftp/python/3.7.0/Python-3.7.0.tar.xz
tar xf Python-3.7.0.tar.xz
cd Python-3.7.0
./configure
make -j3
# Create an altinstall script for use with checkinstall
make -n altinstall > altinstall_script.sh
chmod +x altinstall_script.sh
# Create a .debian file for this python and install it
sudo checkinstall ./altinstall_script.sh
# Change any default values of 'python' to 'python3.7'

# Output:
#**********************************************************************
#
# Done. The new package has been installed and saved to
#
# /root/src/Python-3.7.0/python3.7_3.7.0-1_amd64.deb
#
# You can remove it from your system anytime using:
#
#      dpkg -r python3.7
#
#**********************************************************************


# Download and/or install important scripts
cd ~/scripts
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3.7 get-pip.py --user
curl https://raw.githubusercontent.com/sdispater/poetry/master/get-poetry.py -o get-poetry.py
sudo python3.7 get-poetry.py
```
