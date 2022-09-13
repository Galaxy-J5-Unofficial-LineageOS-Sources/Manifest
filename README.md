# SAMSUNG Galaxy J5 | Build Instructions with Manifest
<br/>

Set up Linux environment
```
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest/lineage-19.1-permissive-GApps/Scripts/environment.sh > environment.sh
sh environment.sh
```
<br/>

Initialize repo:
```
mkdir -p ~/android/lineage
cd ~/android/lineage
repo init -u https://github.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest.git -b lineage-19.1-permissive-GApps
```
<br/>


Download latest manifest:
```
mkdir -p .repo/local_manifests
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/lineage-19.1-permissive-GApps/Manifests/manifest.xml > .repo/local_manifests/manifest.xml
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest/lineage-19.1-permissive-GApps/Manifests/gapps.xml > .repo/local_manifests/gapps.xml
```
<br/>

Sync repo:
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
source build/envsetup.sh
```
<br/>

Patches:

```art```
```
patch -d art -p1 < .repo/manifests/patches/art/art.patch
```

```external/perfetto```
```
patch -d external/perfetto -p1 < .repo/manifests/patches/external_perfetto/perfetto.patch
```

```frameworks/base```
```
patch -d frameworks/base/ -p1 < .repo/manifests/patches/frameworks_base/0023-Add-support-for-app-signature-spoofing.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0013-SystemUI-Always-refresh-power-menu-on-UI-mode-change.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0021-monet-Fix-overly-low-chroma-for-tones-below-90.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0006-Keyguard-Never-switch-to-large-clock.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0001-Hack-Ignore-SensorPrivacyService-Security-Exception.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0002-Bring-Back-XML-Format-UTF-8-TWRP.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0001-Fix-Brightness-Slider-12.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0002-Disable-vendor-mismatch-warning.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0012-core-Remove-old-app-target-SDK-dialog.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0001-camera_extensions.patch
```

```frameworks/native```
```
patch -d frameworks/native -p1 < ".repo/manifests/patches/frameworks_native/0001-SurfaceFlinger-Don't-cleanup-resources-from-previous-frame.patch"
```

``` hardware/interfaces ```
```
repopick -P hardware/interfaces 320531-320532       # twelve-qcom-cam
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_interfaces/0001-interfaces_drop_qti_camera_device_defaults.patch
```

``` packages/apps/Trebuchet```
```
patch -d packages/apps/Trebuchet -p1 < .repo/manifests/patches/packages_apps_Trebuchet/0001-launcher-Add-support-for-themed-icons.patch
```

```packages/modules/adb```
```
patch -d  packages/modules/adb/ -p1 < .repo/manifests/patches/packages_modules_adb/adb.patch
```

```system/bpf```
```
patch -d system/bpf -p1 < .repo/manifests/patches/system_bpf/bpf.patch
```

```system/core```
```
repopick -P system/core 318817
```

```system/netd```
```
patch -d system/netd -p1 < .repo/manifests/patches/system_netd/netd.patch
```

```vendor/lineage```
```
patch -d vendor/lineage -p1 < .repo/manifests/patches/vendor_lineage/0001-Restore-libbfqio-for-non-BPF-devices.patch
repopick -P vendor/lineage 320546
```

```vendor/partner_gms ```
```
patch -d vendor/partner_gms -p1 < .repo/manifests/patches/vendor_partner_gms/0001-Minimal-GMS-For-J5-Devices.patch
```
<br/>

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
