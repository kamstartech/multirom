# MultiROM - Enhanced with Logical Partition Support

MultiROM is a one-of-a-kind multi-boot solution enhanced for **modern Android ROMs with logical partitions**. It can boot Android ROMs while keeping the primary ROM intact, or boot alternative systems without formatting the device. This enhanced version supports **TWRP 3.7.1** and **dynamic/logical partitions** for Android 9+ ROMs.

## 🚀 **Enhanced Features (kamstartech version)**

### ✅ **Logical Partition Support**
- **Dynamic Partitions** - Full support for super partition and logical volumes
- **Modern ROM Support** - Compatible with LineageOS 22+ and Android 15
- **Hybrid Mounting** - Seamless handling of both physical and logical partitions
- **Enhanced ROM Detection** - Automatic partition type detection and handling

### ✅ **TWRP 3.7.1 Integration**
- **Native Integration** - Built specifically for TWRP 3.7.1
- **Modern UI** - Enhanced interface for logical partition ROMs
- **Improved Performance** - Optimized for modern hardware (SDM845+)
- **Better Error Handling** - Enhanced debugging and error reporting

### ✅ **Advanced Capabilities**
- **Kexec Support** - Proper memory management for multi-boot scenarios
- **Modern Encryption** - Enhanced support for File-Based Encryption (FBE)
- **Security Contexts** - Updated for modern Android security requirements
- **Build System** - Enhanced Android.mk for TWRP 3.7.1 compatibility

## 📱 **Tested Devices**

- **Xiaomi Mi Mix 3 (Perseus)** - Snapdragon 845 with logical partitions
- **Compatible with**: Modern devices using dynamic partitions

## 🔗 **Related Repositories**

Complete TWRP 3.7.1 + MultiROM stack:
- **Recovery**: [kamstartech/android_bootable_recovery](https://github.com/kamstartech/android_bootable_recovery)
- **Device Tree**: [kamstartech/twrp-device_xiaomi_perseus](https://github.com/kamstartech/twrp-device_xiaomi_perseus)
- **MultiROM**: [kamstartech/multirom](https://github.com/kamstartech/multirom) (this repo)

## 🛠️ **Build Instructions**

### Prerequisites
Set up TWRP 3.7.1 build environment:
```bash
repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync -j8
```

### Add Enhanced MultiROM
Add to `.repo/local_manifests/roomservice.xml`:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <!-- Enhanced MultiROM with logical partition support -->
  <project path="system/extras/multirom" 
           name="kamstartech/multirom" 
           remote="github" 
           revision="android-9.0-logical-partition-support" />
           
  <!-- libbootimg dependency -->
  <project path="system/extras/libbootimg" 
           name="Tasssadar/libbootimg" 
           remote="github" 
           revision="master" />
</manifest>
```

### Build Commands
```bash
# Set up environment
export ALLOW_MISSING_DEPENDENCIES=true
. build/envsetup.sh
lunch twrp_perseus-eng  # or your device

# Build MultiROM components
make -j$(nproc) multirom trampoline

# Build installation ZIP
make -j$(nproc) multirom_zip
```

## 📊 **Version History**

- **android-9.0-logical-partition-support** - Enhanced version with logical partition support
- **android-9.0** - Base version from vasishath fork
- **Original** - Tasssadar's MultiROM project

## 🎯 **Key Enhancements**

| Component | Enhancement |
|-----------|-------------|
| **multirom.c** | Logical partition detection and ROM installation |
| **multirom_ui.c** | Enhanced UI with partition type awareness |
| **trampoline.c** | Modern boot process for logical partitions |
| **rom_quirks.c** | Updated quirks for LineageOS 22+ ROMs |
| **lib/util.c** | Logical partition utilities and helpers |
| **lib/framebuffer.c** | Modern display handling |
| **Android.mk** | TWRP 3.7.1 build compatibility |

## 🙏 **Credits**

- **Tasssadar** - Original MultiROM creator
- **vasishath** - Android 9.0 port and enhancements
- **kamstartech** - Logical partition support and TWRP 3.7.1 compatibility

## 📞 **Support**

- **Target**: Modern Android devices with dynamic partitions
- **Primary Test Device**: Xiaomi Mi Mix 3 (Perseus)
- **TWRP Version**: 3.7.1+
- **Android Version**: 9.0+ with logical partitions

---
**Enhanced for the community by [@kamstartech](https://github.com/kamstartech)** 🚀
