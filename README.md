# openconnect-proxy

This image provides an easy way to access your home/corporate network through a local SOCKS proxy over the available VPN gateway: run the vpn client in an container and use that connection from the host through a SOCKS5 proxy (dante)

```
docker run --rm --privileged \
           -p 1080:1080 -ti \
           fopina/openconnect-proxy \
           MY.VPN.COM -g VPN_GROUP -u VPN_USERNAME
```

Then `curl -x socks5://127.0.0.1:1080 ipinfo.io` should yield your VPN exit IP.

### IMPORTANT

This is meant to be used in a container available only to the host machine.

Dante-server configuration is wide-open assuming there are no connections to it except from the container host. Do review these if that is not the case.
