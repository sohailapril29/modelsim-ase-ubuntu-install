
#  ModelSim ASE Installation on Ubuntu (64-bit)

ModelSim ASE (**Altera Starter Edition**) is the free version of the **ModelSim HDL simulator**, widely used for **VHDL, Verilog, and SystemVerilog** simulation in **FPGA and VLSI design**.  

Since ModelSim ASE is a **32-bit application**, you need to enable 32-bit architecture and install compatibility libraries when running on **64-bit Ubuntu (20.04 / 22.04 / 24.04)**.  

This guide provides a **step-by-step installation process** and **fixes for common errors**.

---

## 📦 Installation Steps

```bash
# 1. Open and edit .bashrc (optional, for environment variables)
vim ~/.bashrc
source ~/.bashrc

# 2. Go to Downloads folder
cd ~/Downloads

# 3. Make ModelSim installer executable
chmod +x ModelSimSetup-20.1.1.720-linux.run 

# 4. Run the installer
./ModelSimSetup-20.1.1.720-linux.run 

# 5. Navigate to ModelSim ASE bin directory
cd /media/sohail/sohails/modelsim/modelsim_ase/bin

# 6. Try running vsim
./vsim
````

---

## 🛠️ Fixing Missing Libraries

If you see errors like:

```
error while loading shared libraries: libXext.so.6: cannot open shared object file
```

Run these commands:

```bash
# Enable 32-bit architecture
sudo dpkg --add-architecture i386
sudo apt-get update

# Install 32-bit X11 and font libraries
sudo apt-get install libxext6:i386 libxft2:i386 libx11-6:i386 libxrender1:i386 libfontconfig1:i386

# Install core 32-bit runtime libraries
sudo apt-get install libc6:i386 libstdc++6:i386

# Install legacy ncurses5 (required by ModelSim ASE)
sudo apt-get install libncurses5:i386
```

🔍 Verify missing libraries:

```bash
ldd /media/sohail/sohails/modelsim/modelsim_ase/linux/vish | grep "not found"
```

---

## ▶️ Running ModelSim

```bash
cd /media/sohail/sohails/modelsim/modelsim_ase/bin
./vsim
```

If everything is installed correctly, the **ModelSim GUI** will launch. 🎉




![Logo](https://avatars.githubusercontent.com/u/118208461?v=4)


## Authors

- [@sohailapril29](https://github.com/sohailapril29)

