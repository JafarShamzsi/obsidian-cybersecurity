Wireless Network Installation Considerations

Wireless network installation considerations refer to the factors that ensure good availability of authorized Wi-Fi access points. A network with patchy coverage is vulnerable to rogue and evil twin attacks.

The 5 GHz band has more space to configure nonoverlapping channels. Also note that a WAP can use bonded channels to improve bandwidth, but this increases risks from interference.

### Wireless Access Point (WAP) Placement

An infrastructure-based wireless network comprises one or more wireless access points, each connected to a wired network. The access points forward traffic to and from the wired switched network. Each WAP is identified by its MAC address, also referred to as its basic service set identifier (BSSID). Each wireless network is identified by its name or service set identifier (SSID).

Wireless networks can operate in either the 2.4 GHz or 5 GHz radio band. Each radio band is divided into a number of channels, and each WAP must be configured to use a specific channel. For performance reasons, the channels chosen should be as widely spaced as possible to reduce interference.

### Site Surveys and Heat Maps

The coverage and interference factors mean that WAPs must be positioned and configured to cover the whole area with the least overlap as possible. A site survey is used to measure signal strength and channel usage throughout the area to cover. A site survey starts with an architectural map of the site, with features that can cause background interference marked. These features include solid walls, reflective surfaces, motors, microwave ovens, and so on. A Wi-Fi-enabled laptop or mobile device with Wi-Fi analyzer software installed performs the survey. The Wi-Fi analyzer records information about the signal obtained at regularly spaced points as the surveyor moves around the area.

![A Screengrab of a window titled, Wi-Fi Scanner.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/4574-1692974869615.png)

Description

The three tabs on the top left are scanner (selected), current connection, and wireless statistics. The left pane titled, Filters has four expand buttons: quality, network mode, security, and band. The table on the top-right lists the data including the graph, network name (S S I D), MAC address, vendor, signal strength, signal quality, frequency, network details, achievable, and max rate. The tab graphs is selected in the bottom-right pane. Select graph drop-down is set to signal strength: decibel mill watts. The line graph below plots signal strength in decibel mill watts versus time.

Example output from Lizard System's Wi-Fi Scanner tool. (Screenshot courtesy of Lizard Systems.)

These readings are combined and analyzed to produce a heat map, showing where a signal is strong (green/blue) or weak (red), and which channel is being used and how they overlap. This data is then used to optimize the design by adjusting transmit power to reduce a WAP's range, changing the channel on a WAP, adding a new WAP, or physically moving a WAP to a new location.

![A Screengrab of a window titled, Predictive Test 1 dot s s p r j asterisk hyphen Tomography Site Survey shows a heat graph.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/1859-1692974869752.png)

Description

The left pane titled, Band or Name shows the checkbox, 802 point 11 a n selected. The four sub-checkboxes following it are also selected. The sub-checkboxes are virtual AP hash 1 (5 Gigahertz), virtual AP hash 2 (5 Gigahertz), virtual AP hash 3 (5 Gigahertz), and virtual AP hash 4 (5 Gigahertz). The right pane shows a heat map of a regions consisting of conference room 1, elevator, reception, mechanical, back area, files, and conference room 2. The four callouts in the region are as follows: virtual AP hash 1 (5 Gigahertz), virtual AP hash 2 (5 Gigahertz), virtual AP hash 3 (5 Gigahertz), and virtual AP hash 4 (5 Gigahertz).

An illustration of a heat map.

Example heatmap of an office space with four access points. Colors are used to show signal strength from the access points with the following color scheme: blue shows strong signal strength, green shows good signal strength, yellow shows okay signal strength, and red shows low or no signal strength. Signal strength is affected by distance from the access point and obstructions like metal and stone walls or metal enclosures such as elevators.