## 🛠️ Fixing Vitis 2025.1 GUI Not Opening on Ubuntu 24.04.2

This tutorial explains how to fix the launch issue of Vitis 2025.1.

I found this solution on the **AMD Forum**. The original link is provided at the end.

---

### 🔧 Problem

After installing **Vitis 2025.1** on **Ubuntu 24.04.2 LTS**, the GUI does not open when launching the IDE. No error message is displayed in the terminal or log.

The issue is caused by the libstdc++.so and libstdc++.so.6 libraries.

---

### ✅ Solution

To fix it, you need to use the versions provided by Ubuntu instead of the ones bundled with Vitis.

---

### 📝 Step-by-Step Instructions:

1. Open a terminal and navigate to your Vitis installation directory:

   In my case: ```cd /opt/Vivado25/2025.1/Vitis/lib/lnx64.o/Ubuntu```
   
2. Rename the libraries:
 
   ```mv libstdc++.so libstdc++.so.BKP``` and ```mv libstdc++.so.6 libstdc++.so.6.BKP```

3. Update the package list:
   
   ```sudo apt update```
   
   ```sudo apt install libstdc++6``` or  ```sudo apt install libstdc++6:amd64```
---

### ✅ Expected Result

After renaming the libraries and installing the one provided by Ubuntu, the Vitis GUI should launch normally.

---

### 📎 Related Resources

- [AMD Forum](https://adaptivesupport.amd.com/s/question/0D5KZ00000vvAYM0A2/i-am-facing-the-same-problem-with-vitis-20251-and-ubuntu-24042-it-runs-but-the-gui-doesnt-open?language=en_US)
