## 🛠️ Fixing the Vulkan Driver Error in Unreal Engine 5.6 with AMD RX580 on Ubuntu 24.04.3 LTS

This tutorial explains how to fix the Vulkan Driver error in Unreal Engine 5.6 with an AMD RX580 on Ubuntu 24.04.3 LTS.

---

### 🔧 Problem

When creating a new project, the message “Vulkan Driver is required to run the engine” appears because Unreal Engine 5.6 requires Shader Model 6 (SM6), but the AMD RX580 GPU only supports Shader Model 5 (SM5). As shown in the image:

![Message](https://github.com/mcleber/Bug_fixes_and_Configuration_Files/blob/main/Unreal_Engine/image/message.png)

---

### ✅ Solution

To fix the issue, we need to disable SM6 and enable SM5 after creating a new project and seeing the error message.

---

### 📝 Step-by-Step Instructions:

1. Close Unreal Engine if it is open.
  
2. Navigate to your project directory:

```<project_directory>/Config```

3. Open the file `DefaultEngine.ini`.
  
4. Locate the section:

```[/Script/LinuxTargetPlatform.LinuxTargetSettings]```

5. Modify it to use Shader Model 5 instead of 6:

```ini
+TargetedRHIs=SF_VULKAN_SM5
-TargetedRHIs=SF_VULKAN_SM6
```

As shown in the image:

![sm5](https://github.com/mcleber/Bug_fixes_and_Configuration_Files/blob/main/Unreal_Engine/image/sm5.png)

6. Save the file and reopen your project.

---

### ✅ Expected Result

Making these changes will prevent the engine from trying to use SM6 (which the GPU does not support) and eliminate the error message, while keeping Vulkan active and functional.

---

### 📎 Related Resources

- [Unreal Engine](https://www.unrealengine.com/en-US/unreal-engine-5)
