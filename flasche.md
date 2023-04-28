NoNewPrivileges=true
PrivateTmp=true
InaccessibleDirectories=/root /sys /srv -/opt /media -/lost+found
ReadWriteDirectories=/var/minecraft/server

[Install]
WantedBy=default.target
```

`/usr/local/bin/mc-start`:

```
#!/bin/sh

cd /var/minecraft/server
java -Xmx1G -Xms1G \
  -jar server.jar nogui
```

`/usr/local/bin/mc-stop`:

```
#!/bin/sh

/usr/local/bin/rcon stop

while kill -0 $MAINPID 2>/dev/null
do
  sleep 0.5
done
```

`/usr/local/bin/rcon`:

```
#!/bin/sh

mcrcon -H localhost -P 25575 -p "gugus" $@
```

```
sudo systemctl daemon-reload
sudo systemctl enable --now minecraft
```


### Open Port

Finally open the port in the firewall:

```
sudo ufw allow 25565
```

## Configuration Tweaking

Now we are ready to accept configuration tweaking from our friends.

```
motd=Flasche MC Server
max-players=5
white-list=true
enforce-whitelist=true
```

`ops.json`:

```
[
  {
    "uuid": "7f67870f-57d6-406c-9ad1-e848715a9453",
    "name": "technat",
    "level": 4,
    "bypassesPlayerLimit": false
  }
]
```

`whitelist.json`:

```
[
  {
    "uuid": "7f67870f-57d6-406c-9ad1-e848715a9453",
    "name": "technat"
  }
]
```

## Resources
- https://minecraft.fandom.com/wiki/Tutorials/Setting_up_a_server
- https://teilgedanken.de/Blog/post/setting-up-a-minecraft-server-using-systemd/
- https://nolte.github.io/minecraft-infrastructure/index.html
- https://unix.stackexchange.com/questions/302733/minecraft-server-startup-shutdown-with-systemd#303164
