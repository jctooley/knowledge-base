# Services

You can run a python application as a service on a Raspberry Pi.

Create a service called `<service name>.service` with the following code

```console
[Unit]
Description=Minitower oled Service

[Service]
Type=forking
User=root
ExecStart=/bin/bash -c 'python3 /home/pi/Documents/absminitowerkit/temp_light.py &'
Restart=always
RestartSec=30

[Install]
WantedBy=multi-user.target

```

Ensure that you have python and the `py` file located correctly on the `ExecStart` line.

**System Control Commands**

| COMMAND                                | DESCRIPTION                                  |
| -------------------------------------- | -------------------------------------------- |
| `sudo system ctl daemon-reload`        | Reload the daemon after you create a service |
| `sudo systemctl status <service name>` | Get the status of the service                |
| `sudo systemctl start <service name>`  | Start the service                            |
| `sudo systemctl stop <service name>`   | Stop the service                             |
