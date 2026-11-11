# Install and Manage the NIP-05 Service

## 1. Create a systemd service

Open a new systemd service file:

``` bash
sudo nano /etc/systemd/system/nip05.service
```

Paste the following configuration:

``` ini
[Unit]
Description=Cosanostr NIP-05 DNS API
After=network.target

[Service]
Type=simple
User=root
WorkingDirectory=/var/www/cosanostr
ExecStart=/usr/bin/node /var/www/cosanostr/NIP05.js
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

Save the file with **Ctrl+O**, press **Enter**, then exit with
**Ctrl+X**.

## 2. Enable and start the service

Reload systemd, enable the service to start automatically at boot, and
start it now:

``` bash
sudo systemctl daemon-reload
sudo systemctl enable nip05
sudo systemctl start nip05
```

## 3. Check that the service is running

Run:

``` bash
sudo systemctl status nip05
```

You should see:

``` text
Active: active (running)
```

## 4. Useful commands

  Command                            Purpose
  ---------------------------------- ----------------------------
``` bash sudo systemctl start nip05```       Start the API
``` bash sudo systemctl stop nip05```        Stop the API
``` bash sudo systemctl restart nip05```     Restart the API
``` bash sudo systemctl status nip05```      Check the service status
``` bash sudo journalctl -u nip05 -f```      Watch live logs
``` bash sudo journalctl -u nip05 -n 50```   Show the last 50 log lines
