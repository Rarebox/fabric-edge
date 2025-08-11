🚀 Novacoin (NOVA) Chain Kurulum & Test Dökümanı
1️⃣ Gereksinimler
Local (Windows)
Go v1.19.13
📥 https://go.dev/dl/

4 CPU – 8 GB RAM – 20 GB SSD önerilir

Sunucu (Ubuntu 22+)
Minimum: 6 CPU – 12 GB RAM – 100 GB SSD

Go v1.19.13

wget https://go.dev/dl/go1.19.13.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.19.13.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
go version

2️⃣ Proje Derleme

unzip fabric-edge.zip
cd fabric-edge
go build -o NOVA .

3️⃣ Node Dizini Oluşturma

mkdir node1 node2 node3 rpc

4️⃣ Secrets Init (Her Node İçin)

./NOVA secrets init --data-dir ./node1
./NOVA secrets init --data-dir ./node2
./NOVA secrets init --data-dir ./node3
./NOVA secrets init --data-dir ./rpc

💡 Not: Bu komut size Public key ve BLS Public key verecek, genesis komutunda kullanacağız.

5️⃣ Genesis Dosyası Oluşturma

./NOVA genesis \
--max-validator-count 100 \
--name "Novacoin" \
--consensus ibft \
--pos true \
--chain-id 9988 \
--premine=0x2e71530F5C998Ac112aECC2Dc59A1717dB95A6E3:900000000000000000000000000 \
--ibft-validator=0xValidator1Address:BLSKey1 \
--ibft-validator=0xValidator2Address:BLSKey2 \
--ibft-validator=0xValidator3Address:BLSKey3 \
--bootnode=/ip4/IP_NODE1/tcp/1478/p2p/NodeID1 \
--bootnode=/ip4/IP_NODE2/tcp/1479/p2p/NodeID2 \
--bootnode=/ip4/IP_NODE3/tcp/1480/p2p/NodeID3

6️⃣ Node’ları Başlatma

./NOVA server --data-dir ./node1 --block-time 10 --chain ./genesis.json --grpc :10000 --libp2p :10001 --jsonrpc :8545
./NOVA server --data-dir ./node2 --chain ./genesis.json --grpc :11000 --libp2p :11001 --jsonrpc :8546
./NOVA server --data-dir ./node3 --chain ./genesis.json --grpc :12000 --libp2p :12001 --jsonrpc :8547
./NOVA server --data-dir ./rpc --chain ./genesis.json --grpc :13000 --libp2p :13001 --jsonrpc :8548 --seal

Servis Olarak Çalıştırmak İçin (Linux)
/etc/systemd/system/node1.service

[Unit]
Description=Novacoin Node 1
After=network.target

[Service]
User=root
WorkingDirectory=/root/NOVA
ExecStart=/root/NOVA/NOVA server --data-dir /root/NOVA/node1 --chain /root/NOVA/genesis.json --grpc :10000 --libp2p :10001 --jsonrpc :8545
Restart=always
RestartSec=3

[Install]
WantedBy=multi-user.target

sudo systemctl daemon-reload
sudo systemctl enable node1
sudo systemctl start node1

7️⃣ Zincirin Çalıştığını Kontrol Etme

Peer Sayısı

curl -s -X POST http://127.0.0.1:8545 \
-H "Content-Type: application/json" \
--data '{"jsonrpc":"2.0","method":"net_peerCount","params":[],"id":1}'

Son Blok Numarası

curl -s -X POST http://127.0.0.1:8545 \
-H "Content-Type: application/json" \
--data '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}'

Balance Kontrol

curl -s -X POST http://127.0.0.1:8545 \
-H "Content-Type: application/json" \
--data '{"jsonrpc":"2.0","method":"eth_getBalance","params":["0x2e71530F5C998Ac112aECC2Dc59A1717dB95A6E3", "latest"],"id":1}'

💡 İpucu: peerCount > 0 ve blockNumber sürekli artıyorsa zinciriniz sorunsuz çalışıyor.

8️⃣ Explorer ve RPC
RPC URL: https://rpc.novacoin.com

Explorer URL: https://explorer.novacoin.com
