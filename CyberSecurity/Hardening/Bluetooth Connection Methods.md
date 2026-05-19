
Bluetooth is a radio-based wireless technology designed to implement short-range personal area networking. Some security issues associated with Bluetooth include the following:

- **Device Discovery**—is when a device can be put into discoverable mode, meaning that it will connect to any other Bluetooth devices nearby. Unfortunately, even a device in non-discoverable mode can still be detected.
- **Authentication and Authorization**—is when devices authenticate ("pair") using a simple passkey configured on both devices. This should always be changed to some secure phrase and never left as the default, such as "0000." Also, the device's pairing list should be regularly checked to confirm that the devices listed are valid.
- **Malware**—is when there are proof-of-concept Bluetooth worms and application exploits, most notably the BlueBorne exploit ([armis.com/blueborne](https://www.armis.com/blueborne/)), which can compromise any active and unpatched system regardless of whether discovery is enabled and without requiring any user intervention. There are also vulnerabilities in the authentication schemes of many devices. Keep devices updated with the latest firmware.

![A Screengrab of the Settings window shows a dialogue box granting permission to pair a device.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/1261-1692974871218.png) Description

The left pane has a home button followed by a search bar. Below the bar is a list of devices. The right pane is titled, Bluetooth and other devices. A dialog box titled, Pair Device reads, Pair device question mark. The text below reads, Does the PIN on "COMPTIA-MOBILE" match the PIN below question mark, 998584. Two buttons, yes and cancel are present at the bottom.

Pairing a computer with a smartphone. (Screenshot used with permission from Microsoft.)

Using a control center toggle may not actually turn off the Bluetooth radio on a mobile device. If there is any doubt about patch status or exposure to vulnerabilities, Bluetooth should be fully disabled through device settings.

Unless device authentication is configured, a discoverable device is vulnerable to bluejacking, a sort of spam where someone sends you an unsolicited text (or picture/video) message or vCard (contact details). This can also be a vector for malware, as demonstrated by the Obad Android Trojan malware ([securelist.com/the-most-sophisticated-android-trojan/35929](https://securelist.com/the-most-sophisticated-android-trojan/35929/)).

Bluesnarfing refers to using an exploit in Bluetooth to steal information from someone else's phone. The exploit (now patched) allows attackers to circumvent the authentication mechanism. Even without an exploit, a short (four-digit) PIN code is vulnerable to brute force password guessing.

Other significant risks come from the device being connected to another device. A peripheral device with malicious firmware can be used to launch highly effective attacks. This type of risk has a low likelihood as demanding resources are required to craft such malicious peripherals.

### Bluetooth Security Features

Bluetooth incorporates several security features to ensure data and communication security.

 
| Feature                            | Description                                                                                                                                                                                                                                                            |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pairing and Authentication         | During pairing, devices exchange cryptographic keys to authenticate each other's identity and establish a secure communication channel. Pairing is accomplished using various methods, such as numeric comparison, passkey entry, or out-of-band (OOB) authentication. |
| Bluetooth Permissions              | Bluetooth generally requires user consent or permission to connect and access specific services. Users can control which devices connect to their Bluetooth-enabled devices and manage permissions to prevent unauthorized access.                                     |
| Encryption                         | Bluetooth employs encryption algorithms to protect data transmitted between devices. Once pairing is complete, Bluetooth devices use a shared secret key to encrypt data packets.                                                                                      |
| Bluetooth Secure Connections (BSC) | Introduced in Bluetooth 4.0, BSC offers increased resistance against eavesdropping, on-path attacks, and unauthorized access.                                                                                                                                          |
| Bluetooth Low Energy (BLE) Privacy | BLE is a power-efficient version of Bluetooth that uses randomly generated device addresses that periodically change to prevent tracking and unauthorized identification of BLE devices.                                                                               |
