Make screencast working on Firefox, Chromium Snap and wayland with pipewire on focal

```bash
docker build -t screencast-pipewire-focal .
mkdir debs
docker run -it --rm -v ./debs:/debs screencast-pipewire-focal bash -c 'cp /src/*.deb /debs'
# install mutter and its dependencies
find debs -type f | grep -f packages_already_installed.txt -f new_packages.txt | \
    grep -v --regexp=-dev --regexp=-tests | xargs sudo dpkg -i
```

Enable pipewire services:

```bash
systemctl --user --now enable pipewire.service pipewire-media-session.service
```

Reboot.
