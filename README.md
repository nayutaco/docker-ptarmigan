# Ptarmigan Docker

[Ptarmigan](https://github.com/nayutaco/ptarmigan) `Dockerfile` and `Docker Compose`.

We recommend using **Docker Compose**.

## About Docker Compose

Please be sure to put this value.

[options details](https://github.com/nayutaco/ptarmigan/blob/master/docs/ptarmd.md)

- NODE_NAME
    - ptarmd's node name 
- CHAIN
    - mainnet, testnet, regtest
- PORT
    - ptarmigan api port. default 9735
- RPC_PORT
    - bitcoind RPC port.
- RPC_USER
    - bitcoind.conf user
- RPC_PASSWORD
    - bitcoind.conf password
- RPC_URL
    - bitcoind rpc url
- ANNOUNCE_IP
    - ptarmigan local ip address    

### build

```
docker-compose build
```

### up

```
docker-compose up
```

### down

```
docker-compose down 
or
docker-compose down --v
```

### exec

```
docker-compose exec ptarmigan bash
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
