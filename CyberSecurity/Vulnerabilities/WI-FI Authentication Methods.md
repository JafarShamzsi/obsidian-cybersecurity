In order to secure a network, you must confirm that only valid users are connecting to it. Wi-Fi authentication comes in three types: personal, open, and enterprise. Within the personal category, there are two methods: pre-shared key authentication (PSK) and simultaneous authentication of equals (SAE).

### WPA2 Pre-Shared Key Authentication

In WPA2, pre-shared key (PSK) authentication uses a passphrase to generate the key used to encrypt communications. It is also referred to as group authentication because a group of users shares the same secret. When the access point is set to WPA2-PSK mode, the administrator configures a passphrase of between 8 and 63 ASCII characters. This is converted to a 256-bit hash-based message authentication code (HMAC), expressed as a 64-character hex value, using the PBKDF2 key stretching algorithm. This HMAC is referred to as the pairwise master key (PMK). The same secret must be configured on the access point and on each node that joins the network. The PMK is used as part of WPA2's 4-way handshake to derive various session keys.

All types of Wi-Fi personal authentication have been shown to be vulnerable to attacks that allow dictionary or brute force attacks against the passphrase. At a minimum, the passphrase must be at least 14 characters long to try to mitigate risks from cracking.

### WPA3 Personal Authentication

While WPA3 still uses a passphrase to authenticate stations in personal mode, it changes the method the secret uses to agree to session keys. The scheme used is called a Password-Authenticated Key Exchange (PAKE). In WPA3, the Simultaneous Authentication of Equals (SAE) protocol replaces the WPA2 pre-shared key (PSK) method for creating the Pairwise Master Key (PMK). However, the 4-way handshake is still used for key exchange after the PMK is established. SAE uses the Dragonfly handshake, which is basically Diffie-Hellman over elliptic curves key agreement, combined with a hash value derived from the password and device MAC address to authenticate the nodes. With SAE, there should be no way for an attacker to sniff out the handshake to obtain the hash value and try to use an offline brute force or dictionary attack to recover the password. Dragonfly also implements ephemeral session keys providing forward secrecy.

The configuration interfaces for access points can use different labels for these methods. You might see WPA2-Personal and WPA3-SAE rather than WPA2-PSK and WPA3-Personal, for example. Additionally, an access point can be configured for WPA3 only or with support for legacy WPA2 (WPA3-Personal Transition mode). Researchers have found flaws in WPA3-Personal when it is configured in Transition Mode, which allows for downgrade attacks to WPA2. ( [wi-fi.org/security-update-april-2019](https://www.wi-fi.org/security-update-april-2019) ).

### Advanced Authentication

Wireless enterprise authentication modes, such as WPA2/WPA3-Enterprise, include several essential components designed to improve security for corporate wireless networks. One important element is 802.1x authentication, which provides a port-based network access control framework, ensuring that only authenticated devices are granted network access. Typically, 802.1x requires an authentication server such as RADIUS (Remote Authentication Dial-In User Service), which verifies the credentials of users or devices trying to connect to the network.

In enterprise mode authentication schemes, users have a unique set of credentials rather than a shared passphrase as used in WPA2/WPA3 personal mode. Requiring each user or device to authenticate using unique credentials allows network administrators to track network usage at a granular level. The protocol also supports multiple Extensible Authentication Protocol (EAP) types, such as EAP-TLS, EAP-TTLS, or PEAP, which define specific authentication methods. EAP-TLS, for instance, uses client-server certificates for mutual authentication, while EAP-TTLS and PEAP utilize a server-side certificate. The server-side certificate is used to establish a secure tunnel for transmitting user credentials and helps devices validate the legitimacy of the access point. Enterprise mode authentication includes dynamic encryption key management, automatically changing the encryption keys used during a user's session.

### Remote Authentication Dial-In User Service (RADIUS)

The Remote Authentication Dial-In User Service (RADIUS) standard is published as an Internet standard. There are several RADIUS server and client products.

The NAS device (Network Access Server) is configured with the IP address of the RADIUS server and with a shared secret. This allows the client to authenticate to the server. Remember that the client is the access device (switch, access point, or VPN gateway), not the user's PC or laptop. A generic RADIUS authentication workflow proceeds as follows:

1. The user's device (the supplicant) makes a connection to the NAS appliance, such as an access point, switch, or remote access server.
2. The NAS prompts the user for their authentication credentials. RADIUS supports PAP, CHAP, and EAP. Most implementations now use EAP, as PAP and CHAP are not secure. If EAP credentials are required, the NAS enables the supplicant to transmit EAP over LAN (EAPoL) data, but not any other type of network traffic.
3. The supplicant submits the credentials as EAPoL data. The RADIUS client uses this information to create an Access-Request RADIUS packet, encrypted using the shared secret. It sends the Access-Request to the Authentication, Authorization, and Accounting (AAA) server using UDP on port 1812 (by default).
4. The AAA server decrypts the Access-Request using the shared secret. If the Access-Request cannot be decrypted (because the shared secret is not correctly configured, for instance), the server does not respond.
5. With EAP, there will be an exchange of Access-Challenge and Access-Request packets as the authentication method is set up and the credentials verified. The NAS acts as a pass-thru, taking RADIUS messages from the server, and encapsulating them as EAPoL to transmit to the supplicant.
6. At the end of this exchange, if the supplicant is authenticated, the AAA server responds with an Access-Accept packet; otherwise, an Access-Reject packet is returned.

Optionally, the NAS can use RADIUS for accounting (logging). Accounting uses port 1813. The accounting server can be different from the authentication server.