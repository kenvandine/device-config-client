# Device Config Client

A simple client for querying a device-config-client for configuration
values. This client provides utilities for generating configuration
files.

Device serial is expected to be unique, perhaps the value of chassis serial 
in dmidecode which can be found in /sys/class/dmi/id/chassis_serial

## Installation

[![Get it from the Snap Store](https://snapcraft.io/en/dark/install.svg)](https://snapcraft.io/device-config-client)

```
sudo snap install device-config-client
```

# Device Configuration
Supports querying a device-config-client for any available configuraion
values.

Includes gen-landscape-conf to generate a landscape client.conf file populated
for automated registration

## Usage

The client allows setting the server URL for the device-config-client as a
snap setting.

```
snap set device-config-client url=http://SOMEHOST:PORT
```

The server URL can be overridden with the DEVICE_LOOKUP_URL environment variable

```
export DEVICE_LOOKUP_URL=http://SOMEHOST:PORT
```

Query for configuration values for a given device:
```
device-config-client.query SERIAL
```

Query for configuration values for all devices:
```
device-config-client.query
```

Adding record for new device serial. You can find a valid configuration at examples/device.json
```
device-config-client.add SERIAL INPUT_JSON_FILE
```
This JSON file can contain any valid json

# Device Provisioning (autoinstall.yaml)
Supports storing arbitrary key/value configuration as JSON

## Usage

Retrieve stored autoinstall.yaml for a given device:
```
device-config-client.autoinstall SERIAL
```

Adding autoinstall.yaml for new device serial, you can find an valid example at examples/autoinstall.yaml
```
device-config-client.add-autoinstall SERIAL AUTOINSTALL_YAML
```
