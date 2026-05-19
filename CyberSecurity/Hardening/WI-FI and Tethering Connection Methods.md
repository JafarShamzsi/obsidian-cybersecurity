Mobile devices usually default to using a Wi-Fi connection for data, if present. If the user establishes a connection to a corporate network using strong WPA3 security, there is a fairly low risk of eavesdropping or on-path attacks. The risks from Wi-Fi come from users connecting to open access points or possibly a rogue access point imitating a corporate network. These allow the access point owner to launch any number of attacks, even potentially compromising sessions with secure servers (using a DNS spoofing attack, for instance).

### Personal Area Networks (PANs)

Personal area networks (PANs) enable connectivity between a mobile device and peripherals. Ad hoc (or peer-to-peer) networks between mobile devices or between mobile devices and other computing devices can also be established. In terms of corporate security, these peer-to-peer functions should generally be disabled. It might be possible for an attacker to exploit a misconfigured device and obtain a bridged connection to the corporate network.

### Ad Hoc Wi-Fi and Wi-Fi Direct

Wireless stations can establish peer-to-peer connections with one another rather than using an access point. This can also be called an ad hoc network, meaning that the network is not made permanently available. There is no established standards-based support for ad hoc networking, however. MITRE has a project to enable Android smartphones to configure themselves in an ad hoc network ([mitre.org/research/technology-transfer/open-source-software/smartphone-ad-hoc-networking-span](https://www.mitre.org/research/technology-transfer/open-source-software/smartphone-ad-hoc-networking-span)).

Wi-Fi Direct allows one-to-one connections between stations, though in this case, one of the devices actually functions as a soft access point. Wi-Fi Direct depends on Wi-Fi Protected Setup (WPS), which has many vulnerabilities. Android supports operating as a Wi-Fi Direct AP, but iOS uses a proprietary multipeer connectivity framework. You can connect an iOS device to another device running a Wi-Fi Direct SoftAP, however.

There are also wireless mesh products from vendors such as Netgear and Google that allow all types of wireless devices to participate in a peer-to-peer network. These products might not be interoperable, though more now support the EasyMesh standard ([wi-fi.org/discover-wi-fi/wi-fi-easymesh](https://www.wi-fi.org/discover-wi-fi/wi-fi-easymesh)).

### Tethering and Hotspots

A smartphone can share its Internet connection with another device, such as a PC. Where this connection is shared over Wi-Fi with multiple other devices, the smartphone is described as a hotspot. The connection is shared by connecting the smartphone to a PC with a USB cable or with a single PC via Bluetooth, also referred to as tethering. However, the term "Wi-Fi tethering" is quite widely used to mean a hotspot.

This type of functionality would typically be disabled when the device is connected to an enterprise network as it could be used to circumvent security mechanisms such as data loss prevention or web content filtering policies.