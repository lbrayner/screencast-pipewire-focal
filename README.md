Make screencast working on Firefox, Chromium Snap and wayland with pipewire on focal

```bash
docker build -t screencast-pipewire-focal .
mkdir debs
docker run -it --rm -v ./debs:/debs screencast-pipewire-focal bash -c 'cp /src/*.deb /debs'
# install mutter and its dependencies or all packages with the following command
sudo dpkg -i debs/*.deb
```

Enable pipewire services:

```bash
systemctl --user --now enable pipewire.service pipewire-media-session.service
```

Reboot.
