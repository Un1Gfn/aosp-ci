
CircleCI
* [Pipelines](https://app.circleci.com/pipelines/github/Un1Gfn/lineage)
* [Caching](https://circleci.com/docs/2.0/caching/)
* [step - run - WD/shell](https://circleci.com/docs/2.0/configuration-reference/#run)

dpkg
* `-S FILE` which package provide file

[AOSP](https://source.android.com/)
* [Android Community and contacts](https://source.android.com/setup/community.html)
* [Google Git](https://android.googlesource.com/)
* [Android Code Search](https://cs.android.com/)
* [Codename ~ Version ~ API level ~ NDK release](https://source.android.com/setup/start/build-numbers#platform-code-names-versions-api-levels-and-ndk-releases)
* [NDK Revision](https://developer.android.com/ndk/downloads/revision_history)

Nexus 6P
* [XDA](https://forum.xda-developers.com/nexus-6p)
* [kernel](https://forum.xda-developers.com/nexus-6p/help/how-to-make-angler-build-t3262968/page2)

[Partitions and images](https://source.android.com/devices/bootloader/partitions-images)
  * [android-simg2img](https://aur.archlinux.org/packages/android-simg2img/)
  * [simg-tools](https://aur.archlinux.org/packages/simg-tools/)
  * [lineage wiki](https://wiki.lineageos.org/extracting_blobs_from_zips.html)
  * [aosp guide](https://source.android.com/devices/bootloader/partitions-images)

tmux
* Detach: <kbd>Ctrl</kbd>+<kbd>b</kbd> <kbd>d</kbd>

curl
```bash
# Progress meter
curl -LOJR 'https://...'
# Progress bar
curl -# -LOJR 'https://...'
# Silent
curl -sS -LOJR 'https://...'
```

Locale
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
  LANGUAGE = (unset),
  LC_ALL = (unset),
  LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

Save disk space
* [duc](https://duc.zevv.nl/)
  * [usage](https://github.com/zevv/duc/blob/master/doc/duc.md)
  * [AUR](https://aur.archlinux.org/packages/duc/)
  * [xenial](https://packages.ubuntu.com/xenial/duc)
```bash
rm -rfv /var/cache/pacman/*
rm -rfv /var/lib/pacman/sync/*
rm -rfv /var/cache/pkgfile/*"
```

Steal blobs from [factory image](https://developers.google.com/android/images#bullhead)
```bash
sum0="b75ce068f23a0e793805f80fccbc081eca52861ef5eb080c47f502de4c3f9713"
sum1="$(sha256sum angler-opm7.181205.001-factory-b75ce068.zip | cut -d' ' -f1)"
if [ "$sum0" = "$sum1" ]; then
  echo checksum match
else
  echo checksum mismatch
  /usr/bin/false
fi
unset -v sum0
unset -v sum1

cd angler-opm7.181205.001/
unzip image-angler-opm7.181205.001.zip
```

```bash
# file *img
boot.img:                           Android bootimg, kernel (0x8000), ramdisk (0x2000000), page size: 4096, cmdline (androidboot.hardware=angler androidboot.console=ttyHSL0 msm_rtb.filter=0x37 ehci-hcd.park=3 lpm)
recovery.img:                       Android bootimg, kernel (0x8000), ramdisk (0x2000000), page size: 4096, cmdline (androidboot.hardware=angler androidboot.console=ttyHSL0 msm_rtb.filter=0x37 ehci-hcd.park=3 lpm)
system.img:                         Android sparse image, version: 1.0, Total of 786432 4096-byte output blocks in 3898 input chunks.
vendor.img:                         Android sparse image, version: 1.0, Total of 51200 4096-byte output blocks in 845 input chunks.
radio-angler-angler-03.88.img:      data
bootloader-angler-angler-03.84.img: data
```

huawei-angler-opm7.181205.001-52ed73ce.tgz
extract-huawei-angler.sh
```huawei
vendor/
vendor/huawei/
vendor/huawei/angler/
vendor/huawei/angler/BoardConfigPartial.mk
vendor/huawei/angler/device-vendor.mk
vendor/huawei/angler/device-partial.mk
vendor/huawei/angler/proprietary/
vendor/huawei/angler/proprietary/vendor.img
vendor/huawei/angler/android-info.txt
vendor/huawei/angler/BoardConfigVendor.mk
```


<details><summary> *h* </summary>

LineageOS
* [the updater app stores zips in /data/lineageos_updates/](https://wiki.lineageos.org/faq.html#where-does-the-updater-app-store-the-downloaded-zip)
* [Build status](https://www.lineageoslog.com/build)

[Build LineageOS for angler](https://wiki.lineageos.org/devices/angler/build)
* angler tree
  * [device tree](https://github.com/LineageOS/android_device_huawei_angler)
  * [kernel](https://github.com/LineageOS/android_kernel_huawei_angler)

[Docker](https://www.docker.com/)
* Privileged is evil [<sup>O</sup>]() [<sup>O</sup>]() [<sup>O</sup>]() [<sup>O</sup>]() [<sup>O</sup>]()
* [Migration from docker to machine](https://circleci.com/docs/2.0/docker-to-machine/)
* [wikipedia](https://en.wikipedia.org/wiki/Docker_(software))
* [Travis guide](https://docs.travis-ci.com/user/docker/)
* [get into docker](https://stackoverflow.com/questions/30172605/how-do-i-get-into-a-docker-containers-shell)
* [SSH into docker](https://phase2.github.io/devtools/common-tasks/ssh-into-a-container/)
* CLI reference
  * [docker pull](https://docs.docker.com/engine/reference/commandline/pull/)
  * [docker run](https://docs.docker.com/engine/reference/commandline/run/)
  * [docker exec](https://docs.docker.com/engine/reference/commandline/exec/)

Check container capabilities
```bash
# https://stackoverflow.com/questions/46212787/how-to-correctly-report-available-ram-within-a-docker-container
cat /sys/fs/cgroup/memory/memory.limit_in_bytes
ls -Al /
df -h
```

</details>

