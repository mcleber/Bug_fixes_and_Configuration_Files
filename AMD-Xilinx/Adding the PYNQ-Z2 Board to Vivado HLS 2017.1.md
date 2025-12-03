## 🛠️ Adding the PYNQ-Z2 Board to Vivado HLS 2017.1

This guide shows how to manually add support for the PYNQ-Z2 board inside Vivado HLS 2017.1, allowing you to synthesize C/C++ projects targeting the Zynq XC7Z020 device.

---

### 🧩 Problem

Vivado HLS 2017.1 does not include the PYNQ-Z2 board definition by default.
Without this, HLS cannot properly configure projects for the board’s SoC part (xc7z020clg400-1).

---

### ✅ Solution

Add the PYNQ-Z2 entry manually to the file:

```VivadoHls_boards.xml```

After modifying this file, Vivado HLS will recognize the board normally.

---

### 📝 Step-by-step Instructions (Linux)
1. Open a terminal
2. Edit the board configuration file

Run the command below, adjusting the installation path to match your system:

```sudo nano /opt/Xilinx17/Vivado_HLS/2017.1/common/config/VivadoHls_boards.xml```

3. Add the PYNQ-Z2 entry

Scroll to the end of the file and insert the following line:

```<board name="PYNQ-Z2" display_name="PYNQ-Z2" family="zynq" part="xc7z020clg400-1" device="xc7z020" package="clg400" speedgrade="-1" vendor="pynq.io"/>```

4. Save and exit

```Press Ctrl+O → Enter```

```Press Ctrl+X to exit Nano```

Vivado HLS 2017.1 will now recognize PYNQ-Z2 in the board selection menu when creating new projects.

---

### 🪟 Instructions for Windows

The same procedure applies:

Localize the file, usually in:

```C:\Xilinx\Vivado_HLS\2017.1\common\config\VivadoHls_boards.xml```

Open it with Notepad or VS Code (as Administrator).

Add this line at the end:

```<board name="PYNQ-Z2" display_name="PYNQ-Z2" family="zynq" part="xc7z020clg400-1" device="xc7z020" package="clg400" speedgrade="-1" vendor="pynq.io"/>```

Save and restart Vivado HLS.

---

### 💡 Additional Tips

Vivado HLS 2017.1 is part of an older toolchain (before Vitis HLS).
It is normal that modern boards like the PYNQ-Z2 do not appear automatically.

If the board still does not show up, check for:

* file permissions;

* XML formatting errors;

* multiple installations of Vivado HLS.
