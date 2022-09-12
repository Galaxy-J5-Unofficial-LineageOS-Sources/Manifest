# SAMSUNG Galaxy J5 | Build Instructions with Manifest
<br/>

Set up Linux environment
```
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest/lineage-20.0-permissive-GApps/Scripts/environment.sh > environment.sh
sh environment.sh
```
<br/>

Initialize repo:
```
mkdir -p ~/android/lineage
cd ~/android/lineage
repo init -u https://github.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest.git -b lineage-20.0-permissive-GApps

```
<br/>


Download latest manifest:
```
mkdir -p .repo/local_manifests
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/lineage-20.0-permissive-GApps/Manifests/manifest.xml > .repo/local_manifests/manifest.xml
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest/lineage-20.0-permissive-GApps/Manifests/gapps.xml > .repo/local_manifests/gapps.xml

```
<br/>

Sync repo:
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
source build/envsetup.sh
```
<br/>

Patches:

```art ```
```
patch -d art -p1 < .repo/manifests/patches/art/art.patch
```

```bionic ```
```
patch -d art -p1 < .repo/manifests/patches/bionic/0001-HACK-allow-text-relocations.patch
patch -d art -p1 < .repo/manifests/patches/bionic/0002-linker-Apply-TARGET_PROCESS_SDK_VERSION_OVERRIDE-on-.patch
patch -d art -p1 < .repo/manifests/patches/bionic/0003-Hack-Ignore-invalid-pthread_t-to-s.patch
patch -d art -p1 < .repo/manifests/patches/bionic/0004-Implement-per-process-target-SDK-version-override.patch
patch -d art -p1 < .repo/manifests/patches/bionic/0005-bionic-Squash-of-pre-P-mutex-behavior-restoration.patch
patch -d art -p1 < .repo/manifests/patches/bionic/0006-bionic-Sort-and-cache-hosts-file-data-for-fast-looku.patch
patch -d art -p1 < .repo/manifests/patches/bionic/0007-bionic-Support-wildcards-in-cached-hosts-file.patch
patch -d art -p1 < .repo/manifests/patches/bionic/0008-Restore-Shim.patch
```

```frameworks/base ```
```
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0002-Disable-vendor-mismatch-warning.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0012-core-Remove-old-app-target-SDK-dialog.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0001-Revert-Fix-process-group-of-webview-zygote.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/fw.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0003-Add-support-for-app-signature-spoofing.patch
```

```frameworks/libs/net ```
```
patch -d frameworks/libs/net -p1 < .repo/manifests/patches/frameworks_libs_net/0001-bpfheaders-don-t-abort-if-mMapFd-0.patch
patch -d frameworks/libs/net -p1 < .repo/manifests/patches/frameworks_libs_net/0001-Restore-isBPF-supported-for-T.patch
```

```frameworks/native ```
```
patch -d frameworks/native -p1 < .repo/manifests/patches/frameworks_native/0001-GraphicBuffer.cpp-hack-don-t-set-handle-to-0.patch
patch -d frameworks/native -p1 < .repo/manifests/patches/frameworks_native/0002-SurfaceFlinger-Don-t-cleanup-resources-from-previous.patch
patch -d frameworks/native -p1 < .repo/manifests/patches/frameworks_native/0003-gpuservice-only-start-if-ro.kernel.ebpf.supported-is.patch
```

```hardware/interfaces ```
```
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_interfaces/0001-Revert-audio-use-binder-threadpool.patch
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_interfaces/0001-Revert-load-bluetooth-aidl.patch
```

```hardware/lineage/interfaces ```
```
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0001-Restore-vendor.lineage.power-1.0-HIDL.patch
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0002-Restore-vendor.lineage.biometrics.fingerprint.inscre.patch
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0003-Restore-power-HAL.patch
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0004-wifi-fix-legacy-HIDL-for-T.patch
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0005-wifi-hidl_struct_util.cpp-convertLegacyWifiChannelWi.patch
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0006-wifi-wifi.h-fix-build-undef-NAN.patch
```

```hardware/qcom-caf/bluetooth ```
```
patch -d hardware/qcom-caf/bt -p1 < .repo/manifests/patches/hardware_qcom_caf_bluetooth/0001.skip_qcom_caf_bt_building.patch
```

```lmkd ```
```
patch -d system/memory/lmkd -p1 < .repo/manifests/patches/system_memory_lmkd/0001-lmkd-fixup.patch
```

```packages/modules/adb```
```
patch -d  packages/modules/adb/ -p1 < .repo/manifests/patches/packages_modules_adb/adb.patch
```

```packages/modules/bluetooth/```
```
patch -d  packages/modules/Bluetooth/ -p1 < .repo/manifests/patches/packages_modules_bluetooth/0002-gd-hci-Ignore-unexpected-status-events.patch
```

```packages/modules/Connectivity```
```
patch -d packages/modules/Connectivity -p1 < .repo/manifests/patches/packages_modules_connectivity/0001-refresh-netd-patch.patch

```

```system/bpf ```
```
patch -d system/bpf -p1 < .repo/manifests/patches/system_bpf/0001-Restore-isBPF-supported-for-T.patch
```

```system/core ```
```
patch -d system/core -p1 < .repo/manifests/patches/system_core/0001-Revert-init-Treat-failure-to-create-a-process-group-.patch
patch -d system/core -p1 < .repo/manifests/patches/system_core/0002-Revert-healthd-charger-allow-home-button-to-wake.patch

```

```system/libhidl ```
```
patch -d system/libhidl -p1 < .repo/manifests/patches/system_libhidl/0001-delete-gBn-sConstructorMap.patch

```

```system/netd ```
```
patch -d system/netd -p1 < .repo/manifests/patches/system_netd/0001-netd-Allow-devices-to-force-add-directly-connected-r.patch
patch -d system/netd -p1 < .repo/manifests/patches/system_netd/0002-Revert-netd-make-BandwidthController-startup-failure.patch
```

```vendor/lineage ```
```
patch -d vendor/lineage -p1 < .repo/manifests/patches/vendor_lineage/0001-Restore-libbfqio-for-non-BPF-devices.patch
```

```vendor/partner_gms ```
```
patch -d vendor/partner_gms -p1 < .repo/manifests/patches/vendor_partner_gms/0001-Minimal-GMS-For-J5-Devices.patch
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
