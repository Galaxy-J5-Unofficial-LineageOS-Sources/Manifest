# SAMSUNG Galaxy J5 | Build Instructions with Manifest
<br/>

Set up Linux environment
```
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest/lineage-18.1-permissive/Scripts/environment.sh > environment.sh
sh environment.sh
```
<br/>

Initialize LineageOS repo:
```
mkdir -p ~/android/lineage
cd ~/android/lineage
repo init -u git://github.com/Galaxy-J5-Unofficial-LineageOS-Sources/Manifest.git -b lineage-18.1-permissive
```
<br/>

Download latest manifest:
```
mkdir -p .repo/local_manifests
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/lineage-18.1-permissive/Manifests/manifest.xml > .repo/local_manifests/manifest.xml
curl https://raw.githubusercontent.com/Galaxy-J5-Unofficial-LineageOS/Manifest/lineage-18.1-permissive/Manifests/LOS-GApps.xml > .repo/local_manifests/gapps.xml
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
