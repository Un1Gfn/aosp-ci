

[updater app store zips in /data/lineageos_updates/](https://wiki.lineageos.org/faq.html#where-does-the-updater-app-store-the-downloaded-zip)

[Build status](https://www.lineageoslog.com/build)

[Pipelines](https://app.circleci.com/pipelines/github/Un1Gfn/lineage)

[Migration from docker to machine](https://circleci.com/docs/2.0/docker-to-machine/)


Bring up docker
```bash
echo "root:1"|sudo chpasswd
su -

docker run -it -m 6.5G --name test archlinux:20200306
docker rm test
docker ps -a

docker start test
docker attach test

docker exec -ti archlinux:20200306 bash
docker exec -ti archlinux:20200306 bash
```

Check container capabilities
```bash
cat /sys/fs/cgroup/memory/memory.limit_in_bytes
```

BASH_ENV
```bash
export update="pacman -Syy --noprogressbar"
export unreg="pacman -D --asdeps"
export partial="pacman -S --needed --nodeps --noprogressbar --noconfirm" # one --nodeps skil ver chk
export gc="pacman -Rssc --noprogressbar --noconfirm \$(pacman -Qdttq)"
export upgrade="pacman -Suu --noprogressbar --noconfirm"
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
  jdk7-openjdk
---
echo
$gc || true
echo
$upgrade
```
