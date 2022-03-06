# SAMSUNG Galaxy J5 | Build Instructions with Manifest
<br/>

Set up Linux environment (Check <a href="https://github.com/Galaxy-J5-Unofficial-LineageOS/Manifest/blob/main/LOS-Build-Environment.md">here</a>)

<br/>

Initialize repo:
```
mkdir -p ~/android/lineage
cd ~/android/lineage
repo init -u git://github.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest.git -b lineage-19.0-permissive
```
<br/>


Download latest manifest:
```
mkdir -p .repo/local_manifests
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/lineage-19.0-permissive/Manifests/manifest.xml > .repo/local_manifests/manifest.xml
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
patch -d frameworks/base/ -p1 < patches/0023-Add-support-for-app-signature-spoofing.patch
```

```ADB Patch ```
```
patch -d  vendor/lineage/ -p1 < patches/0001-TEMP-Disable-ADB-authentication.patch
```


```Monet```
```
patch -d vendor/lineage -p1 < patches/monet_colors.patch
patch -d vendor/lineage -p1 < patches/monet_enable.patch
patch -d frameworks/base -p1 < patches/monet_frameworks.patch
```

```Legacy```
```
patch -d art -p1 < patches/art.patch
patch -d external/perfetto -p1 < patches/perfetto.patch
patch -d system/bpf -p1 < patches/bpf.patch
patch -d system/netd -p1 < patches/netd.patch
repopick -P frameworks/native 321934
```

```Hacks ```
```
patch -d frameworks/base -p1 < patches/sensor.patch
patch -d frameworks/base -p1 < patches/twrp.patch

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
