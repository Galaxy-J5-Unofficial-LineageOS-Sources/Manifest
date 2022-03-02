    repopick -t twelve-monet
    repopick -Q "status:open+project:LineageOS/android_packages_apps_AudioFX+branch:lineage-19.0"
    repopick -Q "status:open+project:LineageOS/android_packages_apps_Etar+branch:lineage-19.0"
    repopick -Q "status:open+project:LineageOS/android_packages_apps_Trebuchet+branch:lineage-19.0+NOT+317783+NOT+318747"
    repopick -t twelve-burnin
    repopick -t twelve-buttons
    repopick -t twelve-fingerprint
    repopick -t twelve-volume-panel-location
    repopick -t twelve-swap-volume-buttons
    repopick -t twelve-camera-button
    repopick -t twelve-navbar-runtime-toggle
    repopick -t twelve-buttons-lights
    repopick -t twelve-keyboard-lights
    repopick -t twelve-statusbar-brightness-and-qs-slider
    repopick -t twelve-powermenu
    repopick -f -P art 318097
    repopick -f 287706 -P external/perfetto
    repopick -f 318458
    repopick -f -P system/bpf 320591
    repopick -f -P system/netd 320592
    repopick 317298 317300
    repopick 318781
    repopick 319630-319634
    repopick 318021 318022 318023
    repopick 317966-317971 318383-318386 318388
    repopick 318459 318605
    repopick 320524
    repopick -t twelve-restore-camera-hal1
    repopick -t twelve-camera-extension
    repopick 320528-320530                              # twelve-qcom-cam
    repopick -P hardware/interfaces 320531-320532       # twelve-qcom-cam
    repopick -t twelve-legacy-camera
    repopick 318826 318828
    repopick -t twelve-monet
    repopick 320514
    repopick -t twelve-legacy-wfd
