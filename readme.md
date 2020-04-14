
LineageOS
* [updater app store zips in /data/lineageos_updates/](https://wiki.lineageos.org/faq.html#where-does-the-updater-app-store-the-downloaded-zip)
* [Build status](https://www.lineageoslog.com/build)

CircleCI
* [Pipelines](https://app.circleci.com/pipelines/github/Un1Gfn/lineage)


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

[Build LineageOS for angler](https://wiki.lineageos.org/devices/angler/build)
* angler tree
  * [device tree](https://github.com/LineageOS/android_device_huawei_angler)
  * [kernel](https://github.com/LineageOS/android_kernel_huawei_angler)

Android sparse image
  * [android-simg2img](https://aur.archlinux.org/packages/android-simg2img/)
  * [simg-tools](https://aur.archlinux.org/packages/simg-tools/)
  * [lineage wiki](https://wiki.lineageos.org/extracting_blobs_from_zips.html)
  * [aosp guide](https://source.android.com/devices/bootloader/partitions-images)

Check container capabilities
```bash
# https://stackoverflow.com/questions/46212787/how-to-correctly-report-available-ram-within-a-docker-container
cat /sys/fs/cgroup/memory/memory.limit_in_bytes
ls -Al /
df -h
```

Pacman
```bash

$update

cat <<"---" | xargs $unreg || true
  llvm-libs
  gcc-libs
  pcre
  gpm
  libpng
  avahi
---

cat <<"---" | xargs $partial
  git rxvt-unicode-terminfo openssh nmap
  wget tree nano vim pv xz unzip lsof pciutils tmux
  jdk8-openjdk sudo base-devel
---

echo
$gc || true

echo
$upgrade

```

Locale?
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
```bash
rm -rfv /var/cache/pacman/*
rm -rfv /var/lib/pacman/sync/*
rm -rfv /var/cache/pkgfile/*"
```

Steal blobs from [factory image](https://developers.google.com/android/images#bullhead)
```bash
wget https://dl.google.com/dl/android/aosp/angler-opm7.181205.001-factory-b75ce068.zip
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

Verify J*
```bash
archlinux-java set java-8-openjdk
archlinux-java status
```


