

[updater app store zips in /data/lineageos_updates/](https://wiki.lineageos.org/faq.html#where-does-the-updater-app-store-the-downloaded-zip)

[Build status](https://www.lineageoslog.com/build)

[Pipelines](https://app.circleci.com/pipelines/github/Un1Gfn/lineage)

[Migration from docker to machine](https://circleci.com/docs/2.0/docker-to-machine/)


```bash
sudo -i docker run --name test -it archlinux:20200306

docker start test
docker attach test


docker exec -ti archlinux:20200306 bash
docker exec -ti archlinux:20200306 bash
```