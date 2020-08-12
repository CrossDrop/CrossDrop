# CrossDrop

**CrossDrop**是一个跨平台的类似于Airdrop的文件传输工具，旨在实现高速、便捷的跨平台文件传输功能

预计将支持macOS, Windows, Linux, Android, ~~iOS(因为我没有iPhone)~~

## Why CrossDrop?

1. 众所周知，Airdrop是Apple生态内非常方便的文件传输工具，但是Airdrop并非开放协议，且运用了[AWDL](https://owlink.org/wiki/)等技术，这使得Windows与Linux/Android设备无法享受Airdrop丝滑的文件传输功能
2. Airdrop协议在Linux/macOS上的已有实现[OpenDrop](https://github.com/seemoo-lab/opendrop),但是**OpenDrop**仅适用于Linux/macOS平台，Android平台尚未实现，[实现了也需要root](https://github.com/seemoo-lab/opendrop/issues/9)
3. Airdrop的alternative AirDroid本人也使用过，但是我认为AirDroid过于庞大（仅对于文件传输功能来说），而且文件传输功能并不好用
4. 微信... 哈..哈哈(我认为是世界上最傻逼的文件传输工具)
5. Telegram: 连接问题，速度可能较慢

## What will CrossDrop do?

1. CrossDrop is **NOT** campatible with Airdrop!!!!
2. 尽可能得实现类似Airdrop丝滑的传输体验

## How does CrossDrop work? (猜想阶段，PoC正在努力)

1. Sender-----BLE--Broadcast ip, port, metainfo(containing UUID, name, filename and etc.)
2. Receiver---BLE--Observer  Receive ip, port, metainfo
3. Receiver---TCP            Connect and check
4. Sender&Receiver--TCP      Verify each other and start file transfer



