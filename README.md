# Clash for Linux


## Manual for amd64

Directly use this repo, do:

```shell
git clone https://github.com/Corgile/Clash-for-Linux.git ClashProxy
cd ClashProxy
```

edit `config.yaml` to specify the dashboard dist path, eg:

```yaml
external-ui: /path/to/ClashProxy/ui/
```

Startup clash


```sh
sudo ./clash -d .
```

Setting up system proxy (omitted).  Visit 127.0.0.1:3684/ui


## Optional

Manage clash as a linux service: 

```shell
sudo vim /etc/systemd/system/clash.service
```

**It is recommended for `clash` running as a backstage process in `tmux` session, which we will have an easy access to its console/logs by `tmux at -t clash`**. Content of clash.service: 

```text
[Unit]
Description=Clash Proxy Service
After=network.target

[Service]
Type=forking
User=你的用户名
WorkingDirectory=/path/to/ClashProxy
ExecStart=/usr/bin/tmux new-session -d -s clash '/usr/bin/sudo /path/to/ClashProxy/clash -d .'
ExecStop=/usr/bin/tmux kill-session -t clash
Restart=always

[Install]
WantedBy=multi-user.target
```

start clash.service on StartUp

```shell
sudo systemctl daemon-reload
sudo systemctl enable clash.service
sudo systemctl start clash.service
```

And do `systemctl restart clash` after any modifications on `config.yaml`


## disclaimer

The `clash` binary file in this repository was download from ~[clash](https://github.com/Dreamacro/clash)~ (deleted), and this repository is only a backup of my personal tool. **I am not the maintainer of clash, and I am not responsible for any damage to your computer caused by the clash file in this repository**.
