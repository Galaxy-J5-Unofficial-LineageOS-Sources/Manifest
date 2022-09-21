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
patch -d bionic -p1 < .repo/manifests/patches/bionic/0001-HACK-allow-text-relocations.patch
patch -d bionic -p1 < .repo/manifests/patches/bionic/0002-linker-Apply-TARGET_PROCESS_SDK_VERSION_OVERRIDE-on-.patch
patch -d bionic -p1 < .repo/manifests/patches/bionic/0003-Hack-Ignore-invalid-pthread_t-to-s.patch
patch -d bionic -p1 < .repo/manifests/patches/bionic/0004-Implement-per-process-target-SDK-version-override.patch
patch -d bionic -p1 < .repo/manifests/patches/bionic/0005-bionic-Squash-of-pre-P-mutex-behavior-restoration.patch
patch -d bionic -p1 < .repo/manifests/patches/bionic/0006-bionic-Sort-and-cache-hosts-file-data-for-fast-looku.patch
patch -d bionic -p1 < .repo/manifests/patches/bionic/0007-bionic-Support-wildcards-in-cached-hosts-file.patch
patch -d bionic -p1 < .repo/manifests/patches/bionic/0008-Restore-Shim.patch
```

```device/lineage/sepolicy```
```
patch -d device/lineage/sepolicy -p1 < .repo/manifests/patches/device_lineage_sepolicy/0001-legacy-camera-HAL1-sepolicy.patch
```

```external/perfetto ```
```
patch -d external/perfetto -p1 < .repo/manifests/patches/external_perfetto/0001-perfetto-Conditionally-remove-version-check-for-memf.patch
```

```frameworks/av ```
```
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0001-libcameraservice-massive-revert-to-Android-12-state.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0001-Revert-Camera-Remove-old-recording-path-support.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0002-Camera-Restore-camera-HALv1-support-1-2.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0003-Camera-Add-extensions-to-CameraClient.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0004-Camera-CameraHardwareInterface-changes-to-support-Ex.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0005-Camera-Miscellaneous-fixes-in-QDataCallback-and-bind.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0006-camera-Only-link-and-use-vendor.qti.hardware.camera..patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0007-nuplayer-Avoid-crash-when-codec-fails-to-load.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0008-camera-Don-t-segfault-if-we-get-a-NULL-parameter.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0009-libstagefright-Support-YVU420SemiPlanar-camera-forma.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0010-stagefright-omx-Don-t-signal-dataspace-change-on-leg.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0011-stagefright-ACodec-Resolve-empty-vendor-parameters-u.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0012-libstagefright-Free-buffers-on-observer-died.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0013-libstagefright-use-64-bit-usage-for-native_window_se.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0014-camera-include-Don-t-override-possible-overlayed-hea.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0015-Camera-check-metadata-type-before-releasing-frame.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0016-stagefright-add-changes-related-to-high-framerates-i.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0017-Camera-Add-support-for-preview-frame-fd.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0018-CameraSource.cpp-support-PIXEL_FORMAT_YUV420SP_NV21.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0001-libstagefright-Fix-memory-leak-due-to-lock-timeout.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0002-Support-legacy-HALv1-camera-in-mediaserver.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0001-Revert-camera-Only-link-and-use.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0001-Revert-Camera-CameraHardwareInterface-changes-to-sup.patch
patch -d frameworks/av -p1 < .repo/manifests/patches/frameworks_av/0001-camera-Allow-to-use-boottime-as-timestamp-reference.patch
```

```frameworks/base ```
```
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0002-Disable-vendor-mismatch-warning.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0012-core-Remove-old-app-target-SDK-dialog.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0001-Revert-Fix-process-group-of-webview-zygote.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/fw.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0003-Add-support-for-app-signature-spoofing.patch

patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0001-camera2-Add-methods-for-backward-compatibility.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0004-CameraServiceProxy-Loosen-UID-check-conditionally.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0007-Revert-Camera-Injection.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0008-Camera-Restore-camera-HALv1-support-2-2.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0009-Camera-Add-feature-extensions.patch
patch -d frameworks/base -p1 < .repo/manifests/patches/frameworks_base/0016-hax-for-gcam-go.patch
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
patch -d frameworks/native -p1 < .repo/manifests/patches/frameworks_native/0003-SurfaceFlinger-Don-t-cleanup-resources-from-previous.patch
patch -d frameworks/native -p1 < .repo/manifests/patches/frameworks_native/0004-SurfaceFlinger-Don-t-cleanup-resources-from-previous.patch
patch -d frameworks/native -p1 < .repo/manifests/patches/frameworks_native/0003-gpuservice-only-start-if-ro.kernel.ebpf.supported-is.patch
```

```hardware/interfaces ```
```
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_interfaces/0001-Revert-audio-use-binder-threadpool.patch
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_interfaces/0001-Revert-load-bluetooth-aidl.patch
repopick -P hardware/interfaces 320531-320532       # twelve-qcom-cam
patch -d hardware/interfaces -p1 < .repo/manifests/patches/hardware_interfaces/0001-interfaces_drop_qti_camera_device_defaults.patch
```

```hardware/lineage/interfaces ```
```
patch -d hardware/lineage/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0001-Restore-vendor.lineage.power-1.0-HIDL.patch
patch -d hardware/lineage/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0002-Restore-vendor.lineage.biometrics.fingerprint.inscre.patch
patch -d hardware/lineage/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0003-Restore-power-HAL.patch
patch -d hardware/lineage/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0004-wifi-fix-legacy-HIDL-for-T.patch
patch -d hardware/lineage/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0005-wifi-hidl_struct_util.cpp-convertLegacyWifiChannelWi.patch
patch -d hardware/lineage/interfaces -p1 < .repo/manifests/patches/hardware_lineage_interfaces/0006-wifi-wifi.h-fix-build-undef-NAN.patch
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
patch -d  packages/modules/Bluetooth/ -p1 < .repo/manifests/patches/packages_modules_bluetooth/0001-Additionally-check-le_set_event_mask-command-resturn.patch
patch -d  packages/modules/Bluetooth/ -p1 < .repo/manifests/patches/packages_modules_bluetooth/0002-gd-hci-Ignore-unexpected-status-events.patch
patch -d  packages/modules/Bluetooth/ -p1 < .repo/manifests/patches/packages_modules_bluetooth/0003-audio_hal_interface-Optionally-use-sysbta-HAL.patch
```

```packages/modules/Connectivity```
```
patch -d packages/modules/Connectivity -p1 < .repo/manifests/patches/packages_modules_connectivity/0001-refresh-netd-patch.patch
patch -d packages/modules/Connectivity -p1 < .repo/manifests/patches/packages_modules_connectivity/0001-Fix-systemUI-reboot.patch
```


```packages/modules/NetworkStack```
```
patch -d packages/modules/NetworkStack -p1 < .repo/manifests/patches/packages_modules_NetworkStack/0001-Revert-Enable-parsing-netlink-events-from-kernel-sin.patch
```

```prebuilts/build-tools```
```
repopick -P prebuilts/build-tools 336186
```

```system/bpf ```
```
patch -d system/bpf -p1 < .repo/manifests/patches/system_bpf/0001-Restore-isBPF-supported-for-T.patch
```

```system/core ```
```
patch -d system/core -p1 < .repo/manifests/patches/system_core/0001-Revert-init-Treat-failure-to-create-a-process-group-.patch
patch -d system/core -p1 < .repo/manifests/patches/system_core/0001-Fix-samsung-healthd-building.patch
patch -d system/core -p1 < .repo/manifests/patches/system_core/0002-Revert-healthd-charger-allow-home-button-to-wake.patch
patch -d system/core -p1 < .repo/manifests/patches/system_core/0001-Camera-Add-feature-extensions.patch

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

```vendor/qcom/opensource/commonsys-intf/display ```
```
patch -d vendor/qcom/opensource/commonsys-intf/display -p1 < .repo/manifests/patches/vendor_qcom_opensource_commonsys_intf_display/0001-Revert-Hookup-GRALLOC_HANDLE_HAS_RESERVED_SIZE.patch
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
