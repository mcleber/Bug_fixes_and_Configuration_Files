## 🛠️ Gowin EDA 1.9.12.01 Setup on Ubuntu 24.04.2 LTS

This tutorial shows how to set up Gowin EDA 1.9.12.01 on Ubuntu 24.04.2 LTS and fix the following errors:

- `symbol lookup error...`
- `QXcbIntegration: Cannot create platform OpenGL context...`

---

### 🔧 Problem

The `symbol lookup error...` occurs because the software tries to use an incompatible version of the `libfreetype` library.

This `QXcbIntegration: Cannot create platform OpenGL context...` error occurs because Gowin EDA depends on legacy OpenGL (GLX/EGL) and older system libraries (such as `libcrypto.so.10`) that are not available by default on Ubuntu 24.04 LTS.

---

### ✅ Solution

The solution involves renaming a library, creating a symbolic link to another library, and adjusting library paths.

---

### 📝 Step-by-Step Instructions:

1. Download the software from the Gowin website and extract it. You will need to provide the network interface MAC address to request the license file, which will be sent by email.

2. To fix the `symbol lookup error`, open a terminal and navigate to the installation directory.

   In my case: ```cd /opt/Gowin_V1.9.11_linux/IDE/lib/```

3. Rename the `libfreetype.so.6` library.

   ```sudo mv libfreetype.so.6 libfreetype.so.6.bkp```

4. To fix the `QXcbIntegration: Cannot create platform OpenGL context...` error, while still in the `IDE/lib` directory, create a symbolic link to `libcrypto.so.10` in the `IDE/bin` directory.

   ```sudo ln -s libcrypto.so.10 ../bin/libcrypto.so.10```

5. Add the following environment variables:

   ```
   export QT_QPA_PLATFORM_PLUGIN_PATH=/usr/lib/x86_64-linux-gnu/qt5/plugins
   export QT_QPA_PLATFORM=xcb
   export QT_XCB_GL_INTEGRATION=none
   ```

   To do this via terminal, open the ~/.bashrc file:

   ```nano ~/.bashrc```

   Scroll to the end of the file and paste the variables. Then save the file and apply the changes:

   ```source ~/.bashrc```

6. Install the USB driver. Navigate to the directory:

   ```cd /opt/Gowin_V1.9.12.01_linux/Programmer/Driver/```

   Then run the installer script:

   ```./Gowin_USB_Cable_Installer.sh```

7. Launch Gowin EDA:

   ```./gw_ide```

---

### ✅ Expected Result

After completing these steps, the software should run normally.

---

### 📎 Related Resources

-

