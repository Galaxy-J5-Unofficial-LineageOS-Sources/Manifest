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

```Add support for App Signature Spoofing (This is actually needed by MicroG)```
```
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/main/patches/0023-Add-support-for-app-signature-spoofing.patch > 0023-Add-support-for-app-signature-spoofing.patch
patch -d frameworks/base/ -p1 < 0023-Add-support-for-app-signature-spoofing.patch
```

```ADB Patch ```
```
curl https://raw.githubusercontent.com/chil360/lineage_osprey/lineage-19.0/0001-TEMP-Disable-ADB-authentication.patch > 0001-TEMP-Disable-ADB-authentication.patch
patch -d  vendor/lineage/ -p1 < 0001-TEMP-Disable-ADB-authentication.patch
```
<br/>

Repopicks:
```
# Monet
repopick -t twelve-monet # Enables Android 12 Color Scheme based on Wallpaper

# Legacy
repopick -f -P art 318097 # Conditionally remove version check for memfd_create()
repopick -f 287706 -P external/perfetto
repopick -f 318458
repopick -f -P system/bpf 320591 # Ignore bpf errors for < 4.9 kernels
repopick -f -P system/netd 320592 # Ignore netd errors for < 4.9 kernels

# Camera
repopick -t twelve-restore-camera-hal1
repopick -t twelve-camera-extension
repopick 320528-320530
repopick -P hardware/interfaces 320531-320532
repopick -t twelve-legacy-camera

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
