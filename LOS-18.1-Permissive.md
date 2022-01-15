# SAMSUNG Galaxy J5 | Build Instructions with Manifest
<br/>

Set up Linux environment

Follow <a href="https://github.com/Galaxy-J5-Unofficial-LineageOS/Manifest/blob/main/LOS-Build-Environment.md">this documentation</a>

<br/>

Initialize LineageOS repo:
```
mkdir -p ~/android/lineage
cd ~/android/lineage
repo init -u git://github.com/LineageOS/android.git -b lineage-18.1
```
<br/>

Download latest manifest:
```
mkdir -p .repo/local_manifests
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/main/LOS-18.1-Permissive-Manifest.xml > .repo/local_manifests/j5.xml
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/main/LOS-GApps.xml > .repo/local_manifests/gapps.xml
```
<br/>

Sync repo:
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
source build/envsetup.sh
```
<br/>

OpenGApps configure source
```
sudo apt install git-lfs
git lfs install
repo forall -c git lfs pull
rm ~/android/lineage/vendor/opengapps/build/modules/TrichromeLibrary/Android.mk # This is actually needed for Chrome arm
```
<br/

Build:
```
brunch j5nlte #for SM-J500FN
brunch j5lte #for SM-J500F/G/M/NO/Y
brunch j5ltechn #for SM-J5008
brunch j53gxx #for SM-J500H
```

<br/>
