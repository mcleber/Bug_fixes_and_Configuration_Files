## 🔌 Recognizing the USB-Blaster of DE1-SoC on Ubuntu 24.04 LTS

This tutorial explains how to configure your Ubuntu 24.04 system to properly recognize the **USB-Blaster** cable of the **DE1-SoC** board, allowing programming and debugging through Quartus or other FPGA tools.

---

### 🧩 Problem

On Ubuntu, the USB-Blaster cable for the DE1-SoC may not be automatically detected, preventing the programmer from loading projects onto the FPGA.

---

### ✅ Solution

Create a specific udev rule for the USB-Blaster of the DE1-SoC that grants access without requiring root permissions.

---

## 📝 Step-by-step instructions

1. Connect the DE1-SoC USB-Blaster cable to your computer.

2. Open a terminal and run:

``` lsusb ```
  
Look for a line corresponding to the USB-Blaster device, similar to:

``` Altera Corp. USB-Blaster  [09FB:6001] ```

3. Create the udev rule file:

``` sudo nano /etc/udev/rules.d/51-usbblaster.rules ```

4. Insert the following content:

```
# Original specific rule for DE1-SoC USB-Blaster (commented out)
# SUBSYSTEM=="usb", ATTR{idVendor}=="09fb", ATTR{idProduct}=="6001", MODE="0666"

# Generic rule for all Altera USB devices with vendor ID 09fb
SUBSYSTEM=="usb", ATTR{idVendor}=="09fb", MODE="0666"
```
5. Save the file ``` (Ctrl+O) ``` and exit ``` (Ctrl+X) ```.

6. Reload the udev rules:
```
sudo udevadm control --reload-rules
sudo udevadm trigger
```
7. Disconnect and reconnect the USB-Blaster cable.

8. Verify the device permissions with:

``` ls -l /dev/bus/usb/*/* | grep 09fb ```

You should see permissions like:

``` crw-rw-rw- ```

---

### 💡 Additional Tips

Add your user to the ``` plugdev ``` group to ensure you have the required permissions:

``` sudo usermod -aG plugdev $USER ```

Then, log out and log back in to apply the changes.

Always run Quartus as a normal user (avoid using ``` sudo ```).

If you continue experiencing problems, check the USB-Blaster cable and confirm your system detects other USB devices.     
