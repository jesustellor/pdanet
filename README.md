# Connecting phone's proxy to Linux machine(computer), pdanet+, NetShare, TetherFuseNet etc..
## This guide outlines the steps to set up PdaNet+ with redsocks, and dnscrypt. We will use systemd-resolved and configure NetworkManager to use it.

### Instructions for proxy connection
- Install redsocks, in arch it could be found in blackarch repo 

```bash 
# after adding blackarch repo, otherwise you will need to use AUR - like yay or paru
sudo pacman -Syu redsocks
```

### Configure Redsocks

- Create or edit the redsocks configuration file at '/etc/redsocks.conf'

```bash
base {
    log_debug = off;
    log_info = on;
    log = "stderr";
    redirector = iptables;
}

redsocks {
    local_ip = 127.0.0.1;
    local_port = 12345;
    ip = 192.168.49.1;
    port = 8000;
    type = socks5;
}
redsocks {
    local_ip = 172.17.0.1;
    local_port = 12345;
    ip = 127.0.0.1;
    port = 9050;
    type = socks5;
}
```


