# [Ptarmigan](https://github.com/nayutaco/ptarmigan) Docker

`Dockerfile` and `Docker Compose`.

We recommend using **Docker Compose**.

## About Docker Compose

Please be sure to put this value.

[options details](https://github.com/nayutaco/ptarmigan/blob/master/docs/ptarmd.md)

- NODE_NAME
    - ptarmigan node name 
- CHAIN
    - mainnet, testnet, regtest
- LIGHTNING_PORT
    - ptarmigan lightning network port. default 9735.
- RPC_PORT
    - bitcoind RPC port.
- RPC_USER
    - bitcoind user
- RPC_PASSWORD
    - bitcoind password
- RPC_URL
    - bitcoind RPC url
- ANNOUNCE_IP
    - ptarmigan global ip address
    
### Create docker network

Please create docker network.

```
docker network create bitcoind_ptarmigan
```

### Build

```
docker-compose build
```

### Up

```
docker-compose up
```

### Down

```
docker-compose down 
or
docker-compose down --v
```

### Exec

```
docker-compose exec ptarmigan bash
```

Default workdir is `/ptarmigan` and default Ptarmigan node is `test`.

ex) run `ptarmcli --getinfo`.

```
root@d106a876b9fb:/ptarmigan/install/test# ../ptarmcli --getinfo
{
 "result": {
  "node_id": "0266b9882df0aeb943d13d8b1e3dd045963272b583e3d70125eef8bc2bd0aa2bd1",
  "node_port": 12345,
  "announce_ip": "172.27.0.4:12345",
  "total_local_msat": 0,
  "block_count": 101,
  "peers": []
 }
}
```

## About Ptarmigan REST API

Ptarmigan have [REST API](https://github.com/nayutaco/ptarmigan/blob/master/docs/howtouse_rest_api.md).

Default port is `3000`.

```
curl -X POST "http://0.0.0.0:3000/getinfo" -H "accept: application/json"
```

API is made by [Swagger](https://swagger.io/).

```
http://0.0.0.0:3000/api
```

## About NBXplorer

https://github.com/dgarage/NBXplorer

ptarmigan <-> NBXplorer <-> bitcoind


## Custom ptarmd

[In this line of docker-entrypoint.sh](https://github.com/nayutaco/docker-ptarmigan/blob/master/ptarm/docker-entrypoint.sh#L18) is run ptarmd.

Can adjust the options to make ptarmd custom.

```
ptarmd [--network=NETWORK] [-p PORT] [-n ALIAS NAME] [-a IPv4 ADDRESS] [-c BITCOIN.CONF]
```

Please see [Ptarmigan documents](https://github.com/nayutaco/ptarmigan/blob/master/docs/ptarmd.md).
