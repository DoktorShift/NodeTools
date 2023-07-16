### How to create a private-trusted zero-conf channel between routing node and personal mobile wallet app (Blixt Wallet)

Overview
```
______________                                            ______________
|            |............................................|            |
|   Routing  |       private, trusted, 0conf channel      |   Blixt    |
|    Node    |............................................|   Wallet   |
|____________|                                            |____________|

[protocol]                                                ChannelAcceptor - Set zero conf peers:
protocol.option-scid-alias=true                           pubkey routing node
protocol.zero-conf=true
```

Activate Dev Screen on Blixt Wallet:
```
Settings -> Name
Set Name: Hampus
New Setting "Go to dev screen" appears
```

Connect Blixt Wallet to Routing Node:
```
Scroll down dev screen to "CONNECTPEER()" button.
Retrieve routing node infos on mobile phone via mempool.space and paste it into field above.
Connect
```

While connected, open private trusted zero conf channel:
```bash
bos open [pubkey] \
        --type private-trusted \
        --avoid-broadcast \
        --set-fee-rate 1 \
        --amount 10000000
        [--external-funding]
```

Move balance to Blixt side (repeat on depletion of Blixt side):
```
On Blixt, create an invoice: lnbc1......
Pay the invoice from the routing node. 
```

Close private trusted zero conf channel:
```bash
# Routing Node:
lncli abandonchannel ....

# Blixt Wallet:
TBD
```