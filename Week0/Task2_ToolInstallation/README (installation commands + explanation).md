#!/bin/bash

# Week 0 – Task 2: Full Tool Installation Script
# This script installs Yosys, Icarus Verilog, GTKWave, Ngspice, Magic, OpenLANE + Docker
# and checks all dependencies.

set -e  # Stop execution if any command fails

echo "Updating package lists..."
sudo apt-get update
sudo apt-get upgrade -y

# ----------------------------
# Install common dependencies
# ----------------------------
sudo apt install -y build-essential clang bison flex libreadline-dev gawk \
tcl-dev libffi-dev git graphviz xdot pkg-config python3 python3-pip \
libboost-system-dev libboost-python-dev libboost-filesystem-dev \
zlib1g-dev m4 tcsh csh libx11-dev tcl-dev tk-dev libcairo2-dev \
mesa-common-dev libglu1-mesa-dev libncurses-dev apt-transport-https \
ca-certificates curl software-properties-common gtkwave iverilog make

# ----------------------------
# 1️⃣ Yosys
# ----------------------------
echo "Installing Yosys..."
git clone https://github.com/YosysHQ/yosys.git
cd yosys
make config-gcc
make
sudo make install
cd ..

# ----------------------------
# 2️⃣ Icarus Verilog (already installed via apt)
# ----------------------------
echo "Icarus Verilog installed via apt."

# ----------------------------
# 3️⃣ GTKWave (already installed via apt)
# ----------------------------
echo "GTKWave installed via apt."

# ----------------------------
# 4️⃣ Ngspice
# ----------------------------
echo "Installing Ngspice..."
# Make sure you have downloaded ngspice-37.tar.gz to the current directory
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
mkdir release
cd release
../configure --with-x --with-readline=yes --disable-debug
make
sudo make install
cd ../..

# ----------------------------
# 5️⃣ Magic
# ----------------------------
echo "Installing Magic..."
git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
sudo make install
cd ..

# ----------------------------
# 6️⃣ OpenLANE + Docker
# ----------------------------
echo "Installing Docker..."
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
sudo docker run hello-world
sudo groupadd docker
sudo usermod -aG docker $USER
echo "Please reboot your system to apply Docker group changes."

# ----------------------------
# Check dependencies
# ----------------------------
echo "Checking installed versions..."
git --version
docker --version
python3 --version
python3 -m pip --version
make --version
python3 -m venv -h

# ----------------------------
# Optional: Install OpenLane PDKs and Tools
# ----------------------------
echo "Installing OpenLane tools..."
cd $HOME
git clone https://github.com/The-OpenROAD-Project/OpenLane
cd OpenLane
make
make test

echo "All tools installed successfully!"

