## Core

- Receiver exposes itself to LAN and BLE
- Sender finds Receivers
- Sender choose Receiver
- LAN Connection test
- file transfer via SFTP

## BLE Protocol

1. Sender starts Bluetooth as client, finding servers
2. Receiver starts Bluetooth as server and starts advertising
3. Sender lists servers, user chooses one target(receiver)
4. Sender connect to one receiver via Bluetooth 

5. Sender send metadata to receiver as follow:
```
{
   "name": "user name",
   "filetype": 0, // 0 means one file, 1 means files, 2 means one directory, 3 means directories
   "filename": [
        "file1.docx",
        "file2.xlsx"
   ],
   "directory":[
        "folder1",
        "folder2"
   ],
   // We only list files and directories in ./ to simplify the metadata
   // For example, file "./folder1/rar1.rar" won't be listed here
   "ips":[
        "192.168.0.50",
        "10.80.1.73"
   ],
   "port": 11451, // ips and port are used to check LAN connection
   "echostr": "random str, length=**6**",
   "time":"timestamp in ms"   
}
```
6. Sender starts a TCP server at 0.0.0.0:11451, reply "pong!"+username when receiving "ping"+echostr
7. Receiver received metadata, test LAN connection:
   1. Receiver try to establish TCP connection with ip listed in metadata.ips
   2. Receiver send "ping"+echostr, expecting "pong!"
   3. if sender received "ping" with correct echostr, reply "pong!" and close TCP server. 
   4. if receiver received "pong!", stop test
   6. if test failed, tell user to switch to the same subnetwork
8. After user confirms receiving, Receiver starts SFTP server
9. Receiver replies to Sender with SFTP server ip, port, username and password(generated randomly) via BLE.
```
{
    "ip": "11.4.5.14",
    "port": 19810,
    "username": xxxx,
    "password": xxxx
}
```
10. Sender connect SFTP server, upload files.


## LAN Protocal
- TODO(🕊)
