# SAMSUNG Galaxy J5 | Build Instructions with Manifest
<br/>

Set up Linux environment (Check <a href="https://github.com/daviiid99/LineageOS_J5-2015/blob/Manifest_S/environment.sh">here</a>)

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
curl https://raw.githubusercontent.com/daviiid99/LineageOS_J5-2015/Manifest_S/j5.xml > .repo/local_manifests/j5.xml
```
<br/>

Sync repo:
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
source build/envsetup.sh
```
<br/>

Temporal Fixes:

```Add support for device tree in mkbootimg```
```
rm -rf system/tools/mkbootimg
git clone -b system_tools_mkbootimg https://github.com/daviiid99/LineageOS_J5-2015 system/tools/mkbootimg
```
<br/>


```Add support for device tree and BOARD_CUSTOM_MBOOTIMG```
```
mkdir -p SPatches
curl https://raw.githubusercontent.com/daviiid99/LineageOS_J5-2015/Manifest_S/0001-Add-support-for-device-tree-and-BOARD_CUSTOM_BOOTIMG.patch > SPatches/0001-Add-support-for-device-tree-and-BOARD_CUSTOM_BOOTIMG.patch
patch -d build/ -p1 <  SPatches/0001-Add-support-for-device-tree-and-BOARD_CUSTOM_BOOTIMG.patch 
```
<br/>

```msm8916-platform CAF repos```
```
rm -rf hardware/qcom-caf/msm8916/display && rm -rf hardware/qcom-caf/msm8916/media && rm -rf hardware/qcom-caf/msm8916/audio
git clone -b samsung_qcom-caf_media_S https://github.com/daviiid99/LineageOS_J5-2015 hardware/qcom-caf/msm8916/media
git clone -b samsung_qcom-caf_audio_S https://github.com/daviiid99/LineageOS_J5-2015 hardware/qcom-caf/msm8916/audio
git clone -b samsung_qcom-caf_display_S https://github.com/daviiid99/LineageOS_J5-2015 hardware/qcom-caf/msm8916/display
```

Build:
```
brunch j5nlte #for SM-J500FN
brunch j5lte #for SM-J500F/G/M/NO/Y
brunch j5ltechn #for SM-J5008
brunch j53gxx #for SM-J500H
```

<br/>
