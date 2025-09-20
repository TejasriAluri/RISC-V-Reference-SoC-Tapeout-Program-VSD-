# Week 0 – Task 2: Tool Installation & Snapshots

This section documents all the tools installed on my VM for the VSD program, along with version checks and snapshots.

---

## System Details

- RAM: 6 GB  
- Disk: 50 GB  
- vCPU: 4  
- OS: Ubuntu 20.04+

---

## Tools Installed

### 1️⃣ Yosys
**Installation Steps**
```bash
sudo apt-get update
git clone https://github.com/YosysHQ/yosys.git
cd yosys
sudo apt install make build-essential clang bison flex \
libreadline-dev gawk tcl-dev libffi-dev git graphviz xdot \
pkg-config python3 libboost-system-dev libboost-python-dev \
libboost-filesystem-dev zlib1g-dev
make config-gcc
make
sudo make install
2️⃣ Icarus Verilog (iverilog)
sudo apt-get install iverilog
3️⃣ GTKWave
sudo apt install gtkwave
4️⃣ Ngspice
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
mkdir release
cd release
../configure --with-x --with-readline=yes --disable-debug
make
sudo make install
5️⃣ Magic
sudo apt install m4 tcsh csh libx11-dev tcl-dev tk-dev \
libcairo2-dev mesa-common-dev libglu1-mesa-dev libncurses-dev
git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
sudo make install
6️⃣ OpenLANE + Docker
sudo apt install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world
sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot
# After reboot:
docker run hello-world
Additional Checks
git --version
python3 --version
python3 -m pip --version
make --version
python3 -m venv -h

