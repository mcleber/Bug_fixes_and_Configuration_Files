## 🛠️ Installing libncurses5 for Vivado 2025.2.1 on Ubuntu 26.04 LTS

This guide shows how to install the legacy libraries required by Vivado 2025.2.1 on Ubuntu 26.04 LTS.

---

### 🧩 Problem

Vivado 2025.2.1 needs the **libncurses5** library, and **libncurses5** depends on **libtinfo5**.

Ubuntu 26.04 LTS does not provide these packages in its repositories, so they cannot be installed with a plain `sudo apt install libncurses5`.

---

### ✅ Solution

Install the two packages manually, **in this order**:

1. `libtinfo5`
2. `libncurses5`

The `.deb` files are available in the [`libs`](./libs) directory of this repository.

---

### 📝 Instructions

Open a terminal in the folder where you downloaded this repository, then run:

```bash
sudo apt install ./libs/libtinfo5_*.deb
sudo apt install ./libs/libncurses5_*.deb
```

---

### 🔒 Keep Ubuntu from removing them

Ubuntu may later list these packages under `sudo apt autoremove`. To prevent that, mark them as manually installed:

```bash
sudo apt-mark manual libtinfo5 libncurses5
```

---

### 🔍 Checking the installation

```bash
apt policy libtinfo5 libncurses5
```

Expected output:

```
libtinfo5:
  Installed: 6.3-2ubuntu0.3
  Candidate: 6.3-2ubuntu0.3
  Version table:
 *** 6.3-2ubuntu0.3 100
        100 /var/lib/dpkg/status
libncurses5:
  Installed: 6.3-2ubuntu0.3
  Candidate: 6.3-2ubuntu0.3
  Version table:
 *** 6.3-2ubuntu0.3 100
        100 /var/lib/dpkg/status
```

Both packages must show an **Installed** version. The only source listed is `/var/lib/dpkg/status` because the 
packages came from the local `.deb` files, not from an Ubuntu repository. Then open Vivado again.
