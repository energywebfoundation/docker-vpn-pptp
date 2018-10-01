# UTOD - Unsafe Tunnel for Old Devices 

As stated on the title, PPTP based VPNs are not safe to protect from 3rd parties to access the network, data traffic or even the devices on it. This implmentation only serves as a bridge between legacy devices inside a more complex, secured network.

This is a docker image with simple PPTP server with Challenge-Handshake Authentication Protocol (CHAP).

The network adaptor is configured to connect to any `192.168.0.0` network. The gateway is `192.168.250.1` and DHCPs `10-30` network mask `255.255.0.0`.

## Starting VPN server

To start VPN server as a docker container run:

````
docker run -ti --net=host --privileged \
-p 1723:1723 -e client=some_user \
-e server=* -e password=password \
-e acceptable_local_ip_addresses=* \
pauldepraz/utod
````

## Connecting to VPN service
You can use any PPTP client configured to accept CHAP only to connect to the service. To authenticate use credentials provided.


**Note:** Before starting container in `--net=host` mode, please [read how networking in host mode](https://docs.docker.com/network/network-tutorial-host/#prerequisites) works in Docker.

