# Ptarmigan Docker

Ptarmigan's Dockerfile and docker-compose.

We recommend using **docker-compose**.

## About docker-compose

Please be sure to put this value.

[Ptarmigan documment](https://github.com/nayutaco/ptarmigan/blob/master/docs/ptarmd.md)

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

Ptarmigan have REST API.

Default port is `3000`.

```
curl -X POST "http://0.0.0.0:3000/getinfo" -H "accept: application/json"
```

API is made by swagger.

```
http://0.0.0.0:3000/api
```

## About NBXplorer

https://github.com/dgarage/NBXplorer

ptarmigan <-> NBXplorer <-> bitcoind
