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

Temporal Fixes:
```
repopick -P art 318097
repopick -f 287706 -P external/perfetto
repopick 318458
repopick -P system/bpf 320591
repopick -P system/netd 320592
repopick 317298 317300
repopick 318781
repopick 319630-319634
repopick 318021 318022 318023
repopick 317966-317971 318383-318386 318388
repopick 318459 318605
#repopick 317569-317570 317810 317948 318019
repopick -P system/tools/mkbootimg 319780
repopick 320524
repopick -t twelve-restore-camera-hal1
repopick -t twelve-camera-extension
repopick 320528-320530                              
repopick -P hardware/interfaces 320531-320532
repopick -t twelve-legacy-camera
repopick 318826 318828
repopick 320514
repopick -t twelve-legacy-wfd
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
