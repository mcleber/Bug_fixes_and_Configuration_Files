## 🛠️ Adding the PYNQ-Z2 Board to Vivado 2025.2

This guide shows how to manually add support for the **PYNQ-Z2** board inside **Vivado 2025.1**.

---

### 🧩 Problem

Vivado 2025.2 does not include the PYNQ-Z2 board definition by default.

Without this, the board may not appear in the **Boards** tab when creating a new project.

The PYNQ-Z2 uses the following device:

``` text
xc7z020clg400-1
```
---

### ✅ Solution

Install the PYNQ-Z2 board files manually in the Vivado board files directory:

```text
<Vivado installation path>/data/boards/board_files
```
---

### 📝 Instructions for Linux

1. Open a terminal
2. Locate your Vivado 2025.2 installation

Common installation paths are:

```text
/opt/Xilinx/Vivado/2025.2
```

or:

```text
/tools/Xilinx/Vivado/2025.2
```

In newer AMD installations, it may also be something like:

```text
/opt/AMD/Vivado/2025.2
```

Adjust the commands below according to your installation path.

3. Create the board files directory if needed

Example for `/opt/Xilinx/Vivado/2025.2`:

```bash
sudo mkdir -p /opt/Xilinx/Vivado/2025.2/data/boards/board_files
```
4. Download the board files

Download the PYNQ-Z2 board files:

```text
https://github.com/mcleber/Bug_fixes_and_Configuration_Files/tree/main/AMD-Xilinx/boards
```

The final structure should look like this:

```text
/opt/Xilinx/Vivado/2025.2/data/boards/board_files/pynq-z2/A.0/board.xml
/opt/Xilinx/Vivado/2025.2/data/boards/board_files/pynq-z2/A.0/part0_pins.xml
/opt/Xilinx/Vivado/2025.2/data/boards/board_files/pynq-z2/A.0/preset.xml
```
Do not copy only the contents of the `A.0` folder.

Copy the complete `pynq-z2` folder.

5. Restart Vivado

Close Vivado completely and open it again.

Then create a new project and go to:

```text
Create Project > Default Part > Boards
```

Search for:

```text
PYNQ-Z2
```

or:

```text
pynq
```

The board should now appear in the board selection list.

---

### 🪟 Instructions for Windows

The same procedure applies on Windows.

Download the board files.

Then copy the `pynq-z2` folder to the Vivado board files directory.

Common paths are:

```text
C:\Xilinx\Vivado\2025.2\data\boards\board_files
```

or:

```text
C:\AMD\Vivado\2025.2\data\boards\board_files
```

The final structure should be:

```text
C:\Xilinx\Vivado\2025.2\data\boards\board_files\pynq-z2\A.0\board.xml
C:\Xilinx\Vivado\2025.2\data\boards\board_files\pynq-z2\A.0\part0_pins.xml
C:\Xilinx\Vivado\2025.2\data\boards\board_files\pynq-z2\A.0\preset.xml
```

Open Vivado again and check if **PYNQ-Z2** appears in the **Boards** tab.

---

### 🔍 Checking from Vivado Tcl Console

You can also check whether Vivado recognized the board using the Tcl Console.

Inside Vivado, run:

```tcl
get_board_parts *pynq*
```

If the installation worked, Vivado should return an entry related to the PYNQ-Z2 board.

---

### ⚠️ Alternative: Selecting Only the FPGA Part

If the board file does not appear, you can still create a project by selecting the FPGA part manually:

```text
xc7z020clg400-1
```

This allows you to synthesize and implement designs for the PYNQ-Z2 device.

However, selecting only the part is not the same as selecting the board.

When you select only the part, Vivado does not automatically load the PYNQ-Z2 board presets, interfaces, or board-level information.

For simple Verilog projects using a manual `.xdc` constraints file, selecting only the part may be enough.

For projects using the Zynq PS, AXI, Block Design, HDMI, or board presets, installing the board file is recommended.
