## Deprecated
There is a far simpler solution at https://github.com/jedisct1/dnscrypt-proxy/issues/126

Check post #4 by the-w1nd, that init script uses a far more elegant solution using SERVICE_DAEMONIZE=1

Though the START value can be changed from 50 to 21

For more reference regarding DNSCrypt on OpenWRT:

https://github.com/jedisct1/dnscrypt-proxy/issues/162

# dnscrypt-openwrt-init.d-script
Init script for the v2 version of DNScrypt in an OpenWRT env

Requierements:
* Already unpacked/installed dnscrypt-proxy
* OpenWRT shell access
* Basic terminal knowledge

## Usage
The init script can be managed like many others.
```
Syntax: /etc/init.d/dnscrypt-proxy [command]

Available commands:
        start   Start the service
        stop    Stop the service
        restart Restart the service
        reload  Reload configuration files (or restart if that fails)
        enable  Enable service autostart
        disable Disable service autostart
        status  Display the status of the service
```

## Installation
Put the init script 'dnscrypt-proxy' in the /etc/init.d/ directory.
For example, via wget (requires openssl)
```sh
wget -O /etc/init.d/dnscrypt-proxy https://raw.githubusercontent.com/Deka-O/dnscrypt-openwrt-init.d-script/master/dnscrypt-proxy
```
Make it executable
```sh
chmod u+x /etc/init.d/dnscrypt-proxy
```
Configure the values marked with ```###SETUP``` according to you local dnscrypt installation configuration
```sh
NAME="dnscrypt-proxy"
DIR="/opt/$NAME"
###SETUP: Set the directory where your dnscrypt-proxy resides
# Can be commented out/empty if the dnscrypt executable is in $PATH
#
# default: /opt/dnscrypt-proxy

CONF="/etc/config/$NAME/$NAME.toml"
###SETUP: Set the path to your dnscrypt-proxy config
# Can be commented out/empty if a 'dnscrypt-proxy.toml' file exits
# in the same directory as the dnscrypt-proxy executable,
# as that will be used if no config is provided as an argument
#
# default: /etc/config/dnscrypt-proxy/dnscrypt-proxy.toml
```

Enable automatic startup
```sh
/etc/init.d/dnscrypt-proxy enable
```

Start dnscrypt
```sh
/etc/init.d/dnscrypt-proxy start
```

For advanced usage the comments in the script itself are a good next stepping stone.
