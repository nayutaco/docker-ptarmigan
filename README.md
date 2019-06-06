# Ptarmigan Docker

Ptarmigan's Dockerfile and docker-compose.

We recommend using docker-compose.

docker-compose

## docker-compose

Please be sure to put this value.

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

### docker-compose.yml

```docker-compose.yml
version: "3"

services:

  bitcoind:
    restart: unless-stopped
    image: nicolasdorier/docker-bitcoin:0.17.0
    environment:
      BITCOIN_NETWORK: regtest
      BITCOIN_EXTRA_ARGS: |
        rpcuser=ceiwHEbqWI83
        rpcpassword=DwubwWsoo3
        server=1
        rpcport=43782
        port=39388
        whitelist=0.0.0.0/0
        zmqpubrawblock=tcp://0.0.0.0:28332
        zmqpubrawtx=tcp://0.0.0.0:28333
        deprecatedrpc=signrawtransaction
        addresstype=p2sh-segwit
    ports: 
      - "37393:43782"
      - "23823:28332"
    expose:
      - "43782" # RPC
      - "39388" # P2P
    volumes:
      - "bitcoind_dir:/data"
  
  ptarmigan:
    restart: unless-stopped
    stop_signal: SIGKILL
    image: nayutaco/ptarmigan:0.1.0
    environment:
      NODE_NAME: test
      CHAIN: regtest
      PORT: 12345
      RPC_PORT: 43782
      RPC_USER: ceiwHEbqWI83
      RPC_PASSWORD: DwubwWsoo3
      RPC_URL: bitcoind
      ANNOUNCE_IP: ptarmigan
    ports:
      - "3000:3000"
      - "12345:12345"
    expose:
      - "3000"
      - "12345"
    volumes:
      - "bitcoind_dir:/root/.bitcoin"
      - "ptarmigan_dir:/data"
    links:
      - bitcoind
      
volumes:
  bitcoind_dir:
  ptarmigan_dir:
```

#### build

```
docker-compose build
```

#### up

```
docker-compose up
```

#### down

```
docker-compose down 
or
docker-compose down --v
```

#### exec

```
docker-compose exec ptarmigan bash
```

## Ptarmigan REST API

Ptarmigan have REST API.

Default port is `3000`.

```
curl -X POST "http://0.0.0.0:3000/getinfo" -H "accept: application/json"
```

API is made by swagger.

```
http://0.0.0.0:3000/api
```
