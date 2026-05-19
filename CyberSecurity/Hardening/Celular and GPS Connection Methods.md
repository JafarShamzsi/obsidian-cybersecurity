Mobile devices use a variety of connection methods to establish communications in local and personal area networks and for Internet data access via service providers.

![A Screengrab of Microsoft Azure.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/7958-1692974871102.png) Description

The screen is divided into three vertical windows. The first window is titled, create profile. It has fields to fill in the name, description, platform, and profile type. Settings, configure option is selected to open the next window. A create button is at the bottom.  The second window is titled device restrictions, Android. Cellular and connectivity, 8 settings available option is selected to open the next window, Cellular and connectivity, Android. This window displays several options. Each option has two buttons: block and not configured. OK button is present at the bottom right.

Locking down Android connectivity methods with Intune—note that most settings can be applied only to Samsung KNOX-capable devices. (Screenshot used with permission from Microsoft.)

### Cellular/Mobile Data Connections

Smartphones, tablets, and laptops use mobile data networks for data communication. Mobile data connections are unlikely to be subject to monitoring and filtering.

Protecting cellular data connections requires implementing various controls on the endpoints to ensure the security and privacy of corporate data transmitted over cellular networks because mobile data communication effectively bypasses network protections implemented in the enterprise environment. Technologies that protect cellular data connections include user awareness and training, virtual private networks (VPN), mobile device management (MDM), mobile threat defense, and data loss prevention (DLP).

### Global Positioning System (GPS)

A global positioning system (GPS) sensor triangulates the device position using signals from orbital GPS satellites. As this triangulation process can be slow, most smartphones use Assisted GPS (A-GPS) to obtain coordinates from the nearest cell tower and adjust for the device's position relative to the tower. A-GPS uses cellular data. GPS satellites are operated by the US government. Some GPS sensors can use signals from other satellites operated by the European Union (Galileo), Russia (GLONASS), or China (BeiDou).

GPS signals can be jammed or even spoofed using specialist radio equipment. This might be used to defeat geofencing mechanisms for instance ([kaspersky.com/blog/gps-spoofing-protection/26837](https://www.kaspersky.com/blog/gps-spoofing-protection/26837/)).