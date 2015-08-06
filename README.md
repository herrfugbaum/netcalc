[![Dependency Status](https://david-dm.org/slamcode/netcalc.svg)](https://david-dm.org/slamcode/netcalc)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [How to use](#how-to-use)
  - [Installation](#installation)
  - [In your node.js application](#in-your-nodejs-application)
    - [IPv4 To Binary Representation](#ipv4-to-binary-representation)
    - [CIDR Notation To Binary Representation](#cidr-notation-to-binary-representation)
    - [Binary Netmask To Dezimal Netmask](#binary-netmask-to-dezimal-netmask)
    - [IPv4 Min (Network) And Max (Broadcast) Range](#ipv4-min-network-and-max-broadcast-range)
    - [IPv4 Adresses Between and Including Min And Max Adresses](#ipv4-adresses-between-and-including-min-and-max-adresses)
    - [IPv4 Adress into Dezimal Octets](#ipv4-adress-into-dezimal-octets)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## How to use

### Installation

```
npm install netcalc
```

### In your node.js application

```
var netcalc = require('netcalc')
```

#### IPv4 To Binary Representation

```
var ipv4BinaryString = netcalc.ip4ToBinary('192.168.150.1', 'string')
// --> '1100000010101000100101101'

var ipv4BinaryArray = netcalc.ip4ToBinary('192.168.150.1', '')
// --> ['11000000', '10101000', '100101101']
```

#### CIDR Notation To Binary Representation

```
var cidrBinaryBitmaskString = netcalc.cidrToBinaryBitmask(24, 'string')
// --> '1111111111111111111111110'

var cidrBinaryBitmaskArray = netcalc.cidrToBinaryBitmask(24, '')
// --> ['11111111', '11111111', '11111111', '0']
```

#### Binary Netmask To Dezimal Netmask

```
var dezimalNetmask = netcalc.binaryBitmaskToNetmask(['11111111', '11111111', '11111111', '0'], '')
// --> ['255', '255', '255', '0']

var hostpart = netcalc.binaryBitmaskToNetmask(['11111111', '11111111', '11111111', '0'], 'reversed')
// --> ['0', '0', '0', '255']
```

#### IPv4 Min (Network) And Max (Broadcast) Range

```
var ip4Range = netcalc.calculateIp4Range('192.168.150.55', 24)
// --> ['192.168.150.0', '192.168.150.255']
```

#### IPv4 Adresses Between and Including Min And Max Adresses

```
var ip4InnerRange = netcalc.getIp4InnerRange(['192.168.150.0', '192.168.150.255'])
// --> ['192.168.150.0', '192.168.150.1', '192.168.150.2', ... ,'192.168.150.254', '192.168.150.255']
```

#### IPv4 Adress into Dezimal Octets

```
var ip4DezimalOctets = netcalc.ip4Octets('192.168.150.1')
// --> ['192', '168', '150', '1']
```