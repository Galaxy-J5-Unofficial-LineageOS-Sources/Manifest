# SAMSUNG Galaxy J5 | Build Instructions with Manifest
<br/>

Set up Linux environment
```
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest/lineage-19.1-permissive/Scripts/environment.sh > environment.sh
sh environment.sh
```
<br/>

Initialize repo:
```
mkdir -p ~/android/lineage
cd ~/android/lineage
repo init -u https://github.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest.git -b lineage-19.1-permissive
```
<br/>


Download latest manifest:
```
mkdir -p .repo/local_manifests
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/lineage-19.1-permissive/Manifests/manifest.xml > .repo/local_manifests/manifest.xml
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
patch -d frameworks/base/ -p1 < .repo/manifests/patches/0023-Add-support-for-app-signature-spoofing.patch
```

```ADB Patch ```
```
patch -d  vendor/lineage/ -p1 < .repo/manifests/patches/0001-TEMP-Disable-ADB-authentication.patch
```


```Monet```
```
patch -d vendor/lineage -p1 < .repo/manifests/patches/monet_colors.patch
patch -d vendor/lineage -p1 < .repo/manifests/patches/monet_enable.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/monet_frameworks.patch
```

```Legacy```
```
patch -d art -p1 < .repo/manifests/patches/art.patch
patch -d external/perfetto -p1 < .repo/manifests/patches/perfetto.patch
patch -d system/bpf -p1 < .repo/manifests/patches/bpf.patch
patch -d system/netd -p1 < .repo/manifests/patches/netd.patch
repopick -P frameworks/native 321934
```

```Hacks ```
```
patch -d frameworks/base -p1 < .repo/manifests/patches/0001-Hack-Ignore-SensorPrivacyService-Security-Exception.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/0002-Bring-Back-XML-Format-UTF-8-TWRP.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/0001-Fix-Brightness-Slider-12.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/0001-FIX-CRASH-ON-FIRST-J5-BOOT.patch
patch -d frameworks/native -p1 < .repo/manifests/patches/0001-keystore2-fallback-mCallingSid-to-getpidcon.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/0002-Disable-vendor-mismatch-warning.patch
```
<br/>

Build:

```j5nlte```

```
brunch j5nlte #for SM-J500FN
```
<br/>

```j5lte ```

```
brunch j5lte #for SM-J500F/G/M/NO/Y
```
<br/>

```j5ltechn```

```
brunch j5ltechn #for SM-J5008
```
<br/>

```j53gxx```

```
brunch j53gxx #for SM-J500H
```
<br/>

```j5xnlte ```

```
brunch j5xnlte # for SM-J510F
```
<br/>

<br/>
