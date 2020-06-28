
## iOS

## Android
## OSX
## Windows



## How to use QR Code for VoXIP Test

VoXIP test requires setting SIP settings manually, which can be cumbersome and time consuming on a mobile phone. To speed this up We've added an option to read the settings in a JSON format encoded in QR code.
This way you can have multiple settings configuration JSON files and load them fast to VoXIP test using a built-in scanner of QR code.

### Generating QR code 
##### Settings JSON file
First you'll need to create a JSON file with all the settings you want to set. 
All settings are **optional**, so you can create files that change only specific params.
We currently support these settings:

| Field | Type | Description | Example |
| ------ | ------ | ------ | ------ |
| server | String | SIP Proxy | sip-123456.accounts.vocalocity.com |
| user | String | SIP Username | VH123456 |
| password | String | SIP Password | Password1234 |
| port | String | Port to connect to SIP Proxy | 10000 |
| transport | String | SIP transport - Must be TCP/UDP/TLS | TCP |
| stun | String | STUN Server | www.stun.com |
| mmqs | String | MMQS Server (Deprecated, should be empty) | |
| ice | true\|false | Should use ICE (in UCaaS = false) | false |
| dns | true\|false | Should use DNS resolved IPs in SIP messages (in UCaaS = false) | false |

for example:

```json
{
  "server": "sip-123456.accounts.vocalocity.com",
  "user": "VH123456",
  "password": "Password1234",
  "port": "10000",
  "transport": "TCP",
  "stun": "www.stun.com",
  "mmqs": "",
  "ice": false,
  "dns": false
}
```

##### Generate QR on your Mac

While you can take this JSON and convert it to QR code using various Online tools, for conveninece there's a script in "Helpers" folder in VoXIP that allows you just that.
Before running it first time you'll need to install QR-code related python packages:

```sh
pip install qrcode pillow
```

Afterwards you can run the script with this simple syntax:

```sh
./generate_qr_code.sh settings.json
```

The script will automatically open the generated QR-code in PNG format.

##### Scan it on your VoXIP test in iOS or Android

Now you only need to open your Settings screen in iOS or Android VoXIP Test app, and press "Scan QR Code" or "Load from QR". This will open a dedicated scanning screen.
The settings will be automatically updated after the scan. 


## Contributing

Contributions are welcome. Please follow the [contribution guide](CONTRIBUTING.md).