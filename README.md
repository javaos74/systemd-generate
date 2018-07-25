# systemd-generate
How to create systemd native service 



1. create user for service
`
sudo adduser iperf -s /sbin/nologin 
`

2. create service description file 
`
/etc/systemd/system/{myservice}.service
`
cat {myservice}.service
`
[Unit]
Description=Tetration Linux Enforcer
After=network.target

[Service]
Type=simple
Restart=always
RestartSec=1
PIDFile=/var/spool/tet_enforcer/pid/master.pid
WorkingDirectory=/usr/local/tet
ExecStart=/usr/sbin/tet-engine -n tet-enforcer --logtostderr
StandardOutput=null
StandardError=null

[Install]
WantedBy=multi-user.target
`

3. Reload systemd to see the changes 
`
sudo systemctl daemon-reload
`
