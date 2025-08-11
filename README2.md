---

# ----- Coin Planning Document -----

- # Coin Identity

  Coin Name: Novacoin
  Coin Ticker: NOVA
  Chain ID: 9988

- # Coin Numbers

  Total Coins: 900000000
  Block Time: 10
  Total Validators: 100

- # Server IP Addresses

  Server 1:
  Server 2:
  Server 3:
  Server 4 (RPC Server):

- # Genesis File Generation Command

- # Command to Run Daemon on Server

  Server 1: ip1
  Server 2: ip2
  Server 3: ip3
  Server 4 (RPC Server): rpc

- # RPC Details
  Coin Name: Novacoin
  Coin Ticker: Nova
  RPC URL: rpc.novacoin.com
  Chain ID: 9988
  Explorer URL: explorer.novacoin.com

============================================================

- # Node Details

---

## == Node 1 ==

./NOVA secrets init --data-dir node1

---

## == Node 2 ==

./NOVA secrets init --data-dir node2

---

## == Node 3 ==

./NOVA secrets init --data-dir node3

---

## == Node 4 == (rpc)

./NOVA secrets init --data-dir rpc

---

KURULUM -

Gereksinimler

Local için;

https://go.dev/dl/ Buradan go 1.19.13 sürümünü indirip kuracağız.

go build -o NOVA.exe .

mkdir node1, node2, node3, rpc

./NOVA secrets init --data-dir ./node1
./NOVA secrets init --data-dir ./node2
./NOVA secrets init --data-dir ./node3
./NOVA secrets init --data-dir ./rpc

move C:\Users\CAGLAR\.NOVA\* .\node1
move C:\Users\CAGLAR\.NOVA\* .\node2
move C:\Users\CAGLAR\.NOVA\* .\node3
move C:\Users\CAGLAR\.NOVA\* .\rpc

dir genesis.json

./NOVA secrets init --data-dir ~/.NOVA

go version (Kontrol için sürüm doğru mu diye?)

./NOVA.exe genesis --max-validator-count 100 --name "Novacoin" --consensus ibft --pos true --chain-id 9988 --premine=0x2e71530F5C998Ac112aECC2Dc59A1717dB95A6E3:900000000000000000000000000 --ibft-validator=Public key1 (address):BLS Public key --ibft-validator=Public key2 (address):BLS Public key2 --ibft-validator=Public key3 (address):BLS Public key3 --bootnode=/ip4/ip-address/tcp/1478/p2p/Node ID1 --bootnode=/ip4/ip-address/tcp/1479/p2p/Node ID2 --bootnode=/ip4/ip-address/tcp/1480/p2p/Node ID3

.\NOVA.exe server --data-dir .\node1 --chain .\genesis.json --grpc :10000 --libp2p :10001 --jsonrpc :8545

.\NOVA.exe server --data-dir .\node2 --chain .\genesis.json --grpc :11000 --libp2p :11001 --jsonrpc :8546

.\NOVA.exe server --data-dir .\node3 --chain .\genesis.json --grpc :12000 --libp2p :12001 --jsonrpc :8547

.\NOVA.exe server --data-dir .\rpc --chain .\genesis.json --grpc :13000 --libp2p :13001 --jsonrpc :8548 --seal

Sunucu için;

Minimum Gereksinimler;
6 CPU - 12 GB RAM - 100 GB SSD - Ubuntu 22 ve üstü

https://go.dev/dl/go1.19.13.linux-amd64.tar.gz

sudo tar -C /usr/local -xzf go1.19.13.linux-amd64.tar.gz

export PATH=$PATH:/usr/local/go/bin

go version

unzip fabric-edge.zip

go build -o NOVA .

/root/NOVA/NOVA secrets init --data-dir /root/NOVA/node1

/root/NOVA/NOVA secrets init --data-dir /root/NOVA/node2

/root/NOVA/NOVA secrets init --data-dir /root/NOVA/node3

/root/NOVA/NOVA secrets init --data-dir /root/NOVA/rpc

./NOVA genesis --max-validator-count 100 --name "Novacoin" --consensus ibft --pos true --chain-id 9988 --premine=0x2e71530F5C998Ac112aECC2Dc59A1717dB95A6E3:900000000000000000000000000 --ibft-validator=Public key1 (address):BLS Public key --ibft-validator=Public key2 (address):BLS Public key2 --ibft-validator=Public key3 (address):BLS Public key3 --bootnode=/ip4/ip-address/tcp/1478/p2p/Node ID1 --bootnode=/ip4/ip-address/tcp/1479/p2p/Node ID2 --bootnode=/ip4/ip-address/tcp/1480/p2p/Node ID3

./NOVA genesis --max-validator-count 100 --name "Novacoin" --consensus ibft --pos true --chain-id 9988 --premine=0x2e71530F5C998Ac112aECC2Dc59A1717dB95A6E3:900000000000000000000000000 --ibft-validator=Public key1 (address):BLS Public key --ibft-validator=Public key2 (address):BLS Public key2 --ibft-validator=Public key3 (address):BLS Public key3 --bootnode=/ip4/ip-address/tcp/1478/p2p/Node ID1 --bootnode=/ip4/ip-address/tcp/1479/p2p/Node ID2 --bootnode=/ip4/ip-address/tcp/1480/p2p/Node ID3

Bu aşağıdaki yerine örnek olarak service yazarsanız chain hiç durmaz örnek olarak size bir servis göndereceğim.

.\NOVA server --data-dir .\node1 --chain .\genesis.json --grpc :10000 --libp2p :10001 --jsonrpc :8545

.\NOVA server --data-dir .\node2 --chain .\genesis.json --grpc :11000 --libp2p :11001 --jsonrpc :8546

.\NOVA server --data-dir .\node3 --chain .\genesis.json --grpc :12000 --libp2p :12001 --jsonrpc :8547

.\NOVA server --data-dir .\rpc --chain .\genesis.json --grpc :13000 --libp2p :13001 --jsonrpc :8548 --seal
