# OpenVPN Learn Address Script

Script that allows [OpenVPN](https://github.com/OpenVPN/openvpn) to update DNS servers via RFC2136.

The script requires the following to be configured:

* `server`: The hostname of the DNS server.
* `keyName`: The name of the HMAC-MD5 TSIG key.
* `key`: The HMAC-MD5 TSIG key.
* `forwardZone`: The zone to update.
* `ttl`: The TTL to set for records. Defaults to 60.

The script will add forward and reverse DNS records for clients when they connect to OpenVPN. It will remove these records when the client disconnects. The FQDN is based off of the common name and configured forward zone. So if you have `forwardZone` set to `example.local` and the client's common name is `device1`, the record would be for `device1.example.local`. Both IPv4 and IPv6 is supported.

The script is stateless and expects that the records made by it are not modified. The only file operations performed are temporary files for nslookup.

The script should be added to OpenVPN's `learn-address` property, as described [here](https://openvpn.net/community-resources/reference-manual-for-openvpn-2-4).

This program was made for use with [pfSense](https://github.com/pfsense/pfsense). Modification may be required for other platforms.

OpenVPN is a licensed under [the GPLv2 license](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html).  
pfSense is licensed under [the Apache License v2.0](https://www.apache.org/licenses/LICENSE-2.0).
