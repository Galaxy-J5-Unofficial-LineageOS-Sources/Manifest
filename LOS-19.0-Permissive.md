# SAMSUNG Galaxy J5 | Build Instructions with Manifest
<br/>

Set up Linux environment (Check <a href="https://github.com/Galaxy-J5-Unofficial-LineageOS/Manifest/blob/main/LOS-Build-Environment.md">here</a>)

<br/>

Initialize repo:
```
mkdir -p ~/android/lineage
cd ~/android/lineage
repo init -u git://github.com/LineageOS/android.git -b lineage-19.0
```
<br/>


Download latest manifest:
```
mkdir -p .repo/local_manifests
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/main/LOS-19.0-Permissive-Manifest.xml > .repo/local_manifests/j5.xml
```
<br/>

Sync repo:
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
source build/envsetup.sh
```
<br/>

Patches:

```Add support for device tree and BOARD_CUSTOM_MBOOTIMG```
```
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/main/patches/0001-Add-support-for-device-tree-and-BOARD_CUSTOM_BOOTIMG.patch > 0001-Add-support-for-device-tree-and-BOARD_CUSTOM_BOOTIMG.patch
patch -d build/ -p1 < 0001-Add-support-for-device-tree-and-BOARD_CUSTOM_BOOTIMG.patch 
```
<br/>

Repopicks:
```
repopick -P art 318097 # Conditionally remove version check for memfd_create()
repopick -f 287706 -P external/perfetto # Conditionally remove version check for memfd_create()
repopick 318458 # Use AVCProfileMain for screen recorder
repopick -P system/bpf 320591 # Ignore bpf errors for < 4.9 kernels
repopick -P system/netd 320592 # Ignore netd errors for < 4.9 kernels
repopick -P system/tools/mkbootimg 319780 # add support for --dt
repopick -t twelve-monet # Enables Android 12 Color Scheme based on Wallpaper
```
<br/>

Build:
```
brunch j5nlte #for SM-J500FN
brunch j5lte #for SM-J500F/G/M/NO/Y
brunch j5ltechn #for SM-J5008
brunch j53gxx #for SM-J500H
```

<br/>
