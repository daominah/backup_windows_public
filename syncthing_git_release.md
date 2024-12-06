## Homepage

https://github.com/syncthing/syncthing/releases

https://github.com/syncthing/syncthing/blob/main/README-Docker.md

## Windows

SyncThing provides a binary exe,
but this guy helps to install SyncThing as a service (auto run on boot):

https://github.com/Bill-Stewart/SyncthingWindowsSetup/releases

2024-04 v1.27.5:

https://github.com/Bill-Stewart/SyncthingWindowsSetup/releases/download/v1.27.5/syncthing-1.27.5-setup.exe

## Linux

Last check: 2024-10 v1.28.0

```bash
docker run -dit --restart=always --network=host \
    -v /media/tungdt/WindowsData/syncthing:/var/syncthing \
    -e STGUIADDRESS=127.0.0.1:8384 \
    --name syncthing syncthing/syncthing:1.28.0
```

## MacOS

Host network is not supported, so we need to run:

```bash
docker run -dit --restart=always \
    -p 8384:8384 -p 22000:22000/tcp -p 22000:22000/udp -p 21027:21027/udp \
    -v /Users/tungdt/syncthing:/var/syncthing -e STGUIADDRESS=0.0.0.0:8384 \
    --name syncthing syncthing/syncthing:1.28.0
```

After install, need to set up a password on the web interface because of
this way of running SyncThing listens on 0.0.0.0 instead of 127.0.0.1.
