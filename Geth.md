Gethの初期化
geth --datadir /Users/matsumotoayaka/eth_private_net init /Users/matsumotoayaka/eth_private_net/genesis.json

Geth起動
geth --networkid "10" --nodiscover --datadir "/Users/matsumotoayaka/eth_private_net" console 2>> /Users/matsumotoayaka/eth_private_net/geth_err.log
