# Clash for Linux


## Manual for Ubuntu (amd64)

Directly use this repo, do:

```shell
git clone https://github.com/Corgile/clash.git ClashProxy
cd ClashProxy
```

edit `config.yaml` to specify the dashboard dist path, eg:

```yaml
external-ui: /path/to/ClashProxy/ui/
```

Startup clash


```shell
sudo ./clash -d .
```

Setting up system proxy (omitted).  Visit 127.0.0.1:3684/ui


## Optional

If you want a newer version Dashboard:

```shell
git submodule init
git submodule update
cd clash-dashboard

# pull latest repo
git pull origin master

# install dependencies and build
npm i
npm run build  # may need npm install vite -g -S  first
```

Restart Clash.

## Other

visit https://github.com/Dreamacro/clash/releases for a different arch clash binary.

