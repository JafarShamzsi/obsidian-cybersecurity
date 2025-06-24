As well as the site design, a wireless network must be configured with security settings. Without encryption, anyone within range can intercept and read packets passing over the wireless network. Security choices are determined by device support for the various Wi-Fi security standards, by the type of authentication infrastructure, and by the purpose of the WLAN. Security standards determine which cryptographic protocols are supported, the means of generating the encryption key, and the available methods for authenticating wireless stations when they try to join (or associate with) the network.

The first version of Wi-Fi Protected Access (WPA) was designed to fix critical vulnerabilities in the earlier wired equivalent privacy (WEP) standard. Like WEP, version 1 of WPA uses the RC4 stream cipher but adds a mechanism called the Temporal Key Integrity Protocol (TKIP) to make it stronger.

![A Screengrab of a section to personalize settings for each brand or enable Smart Connect to configure the same settings for all bands.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/811-1692974869819.png) 
Description

The settings are as follows. O F D M A is enabled. Smart connect is not enabled. 2.4 Gigahertz is enabled. Network name (S S I D): TP-Link underscore 22DD. Security: WPA slash WPA2-Personal. Version: W P A 2-P S K. Encryption: A E S. Password: tplinkpassword. Transmit power: high. Channel width: auto. Channel: auto. Mode: 802 point 11b slash g slash n mixed. 5 Gigahertz is enabled. Network name (S S I D): TP-Link underscore 22DD underscore 5G. Security: W P A 2/W P A 3-Personal. Version: W P A 3-S A E. Password: tplinkpassword. Transmit power: high. Channel width: auto. Channel: auto. Mode: 802 point 11ax only.

Configuring a TP-LINK SOHO access point with wireless encryption and authentication settings. In this example, the 2.4 GHz band allows legacy connections with WPA2-Personal security, while the 5 GHz network is for 802.11ax (Wi-Fi 6) capable devices using WPA3-SAE authentication. (Screenshot used with permission from TP-Link Technologies.)

### Wi-Fi Protected Setup (WPS)

As setting up an access point securely is relatively complex for residential consumers, vendors have developed a system to automate the process called Wi-Fi Protected Setup (WPS). To use WPS, both the access point and wireless station (client device) must be WPS-capable. Typically, the devices will have a push button. Activating this on the access point and the adapter simultaneously will associate the devices using a PIN, then associate the adapter with the access point using WPA2. The system generates a random SSID and PSK. If the devices do not support the push button method, the PIN (printed on the WAP) can be entered manually.

Unfortunately, WPS is vulnerable to a brute force attack. While the PIN is eight characters, one digit is a checksum and the rest are verified as two separate PINs of four and three characters. These separate PINs are many orders of magnitude simpler to brute force, typically requiring just hours to crack. On some models, disabling WPS through the admin interface does not actually disable the protocol, or there is no option to disable it. Some APs can lock out an intruder if a brute force attack is detected, but in some cases, the attack can just be resumed when the lockout period expires.

To counter this, the lockout period can be increased. However, this can leave APs vulnerable to a denial of service (DoS) attack. When provisioning a WAP, it is essential to verify what steps the manufacturer has taken to make their WPS implementation secure and to use the required device firmware level identified as secure.

The Easy Connect method, announced alongside WPA3, is intended to replace WPS as a method of securely configuring client devices with the information required to access a Wi-Fi network. Easy Connect is a brand name for the Device Provisioning Protocol (DPP).

Each participating device must be configured with a public/private key pair. Easy Connect uses quick response (QR) codes or near-field communication (NFC) tags to communicate each device's public key. A smartphone is registered as an Easy Connect configurator app and associated with the WAP using its QR code. Each client device can then be associated by scanning its QR code or NFC tag in the configurator app. As well as fixing the security problems associated with WPS, this is a straightforward means of configuring headless Internet of Things (IoT) devices with Wi-Fi connectivity.

### Wi-Fi Protected Access 3 (WPA3)

Neither WEP nor the original WPA version is considered secure enough for continued use. WPA2 uses the Advanced Encryption Standard (AES), deployed within the Counter Mode with Cipher Block Chaining Message Authentication Code Protocol (CCM). AES replaces RC4 and CCM replaces TKIP. CCM provides authenticated encryption, which is designed to make replay attacks harder.

Weaknesses found in WPA2 led to its intended replacement by WPA3. The main features of WPA3 are as follows:

- Simultaneous Authentication of Equals (SAE)—replaces the Pre-Shared Key (PSK) exchange protocol in WPA2, ensuring an attacker cannot intercept the Wi-Fi password even when capturing data from a successful login.
- **Enhanced Open**—encrypts traffic between devices and the access point, even without a password, which increases privacy and security on open networks.
- **Updated Cryptographic Protocols**—replaces AES CCM with the AES Galois Counter Mode (GCM) mode of operation. Galois Counter Mode has higher levels of performance than CCM.
- **Wi-Fi Easy Connect**—allows connecting devices by scanning a QR code, reducing the need for complicated configurations while maintaining secure connections.

Wi-Fi performance also depends on device support for the latest 802.11 standards. The most recent generation (802.11ax) is being marketed as Wi-Fi 6. The earlier standards are retroactively named Wi-Fi 5 (802.11ac) and Wi-Fi 4 (802.11n). The performance standards are developed in parallel with the WPA security specifications. Most Wi-Fi 6 devices and some Wi-Fi 5 and Wi-Fi 4 products should support WPA3 either natively or with a firmware/driver update.