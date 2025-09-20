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

**Version Check**
yosys -V
*Snapshot*
<img width="819" height="611" alt="yosys" src="https://github.com/user-attachments/assets/023423d4-1de2-41b3-8798-aec8fa3565b1" />

