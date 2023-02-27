# Usage

Clone any Laravel project into `./src`.

Then run:
```bash
`export UID=$(id -u) && export GID=$(id -g)`
```

```bash
docker-compose up -d --build
```

On some systems it might be necessary to increase swap memory.
```bash
sudo fallocate -l 4G /swapfile; ls -lh /swapfile; sudo chmod 600 /swapfile; sudo mkswap /swapfile; sudo swapon /swapfile; sudo swapon -s; free -m;
```
Then open `/etc/fstab` and add the following line to the end of the file:
```text
/swapfile none swap sw 0 0
```
# If your stack uses InertiaJS there are some pitfalls to consider

This repo is meant to be used behind a nginx reverse proxy. If you are using InertiaJS the `route()`-helper will not generate the appropriate HTTPS Urls. Consider the workarounds suggested in [this issue on the Ziggy repository](https://github.com/tighten/ziggy/issues/410).
