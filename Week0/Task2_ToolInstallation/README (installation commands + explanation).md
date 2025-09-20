**Week 0 – Task 2: Tool Installation & Snapshots**

This document provides a summary of the tools installed on my virtual machine as part of the VSD program. All tools have been installed following the recommended system configuration, and their installation has been verified with snapshots.

**System Configuration**

**RAM:** 6 GB

**HDD:** 50 GB

**CPU:** 4 vCPUs

**OS:** Ubuntu 20.04+

**Virtual Machine**: Oracle VirtualBox 
https://www.virtualbox.org/wiki/Downloads
**Tool check**
**Installed Tools & Installation Steps
### 1. Yosys
**Description:** Yosys is an open-source synthesis tool for Verilog.

**Installation Commands:**
```bash
sudo apt-get update
git clone https://github.com/YosysHQ/yosys.git
cd yosys
sudo apt install make   # If not already installed
sudo apt-get install build-essential clang bison flex \
libreadline-dev gawk tcl-dev libffi-dev git graphviz xdot \
pkg-config python3 libboost-system-dev libboost-python-dev \
libboost-filesystem-dev zlib1g-dev
make config-gcc
make
sudo make install

**### 2. Icarus Verilog (Iverilog)
****Description:** Iverilog is a Verilog simulation and synthesis tool.

**Installation Commands:**
```bash
sudo apt-get update
sudo apt-get install iverilog

