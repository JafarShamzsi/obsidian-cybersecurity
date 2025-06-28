The purpose of device hardening is to enhance a system's security by minimizing the potential vulnerabilities a malicious entity could exploit. This is achieved by configuring network and system settings to reduce their attack surface.

### Segmentation

Segmentation is crucial to securing an enterprise environment because it reduces the potential impact of a cybersecurity incident by isolating systems and limiting the spread of an attack or malware infection. In a segmented network, systems are divided into separate segments or subnets, each with distinct security controls and access permissions. This type of segmentation significantly complicates an attacker's work, giving an organization more time to detect and respond. Furthermore, segmentation allows more granular control over data access to ensure users, devices, and applications only have access to the information necessary for their specific tasks, thus enhancing data protection and privacy.

![A router is connected to two switches. The first switch is a part of the marketing subnet and the second switch is a part of the finance subnet.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/5170-1692974870710.png)

A segmented network showing Marketing and Finance subnets and the placement of network devices. Traffic between the two networks is controlled by the router. (Images © 123RF.com.)

### Isolation

Device isolation refers to segregating individual devices within a network to limit their interaction with other devices and systems. This aims to enhance endpoint protection by preventing the lateral spread of threats should a device become compromised. In the context of endpoint protection, device isolation creates barriers between devices so that a threat that infiltrates one device cannot easily spread to others. Device isolation restricts network traffic between devices reducing the potential attack surface. This approach is particularly useful for threats like worms or ransomware which often aim to propagate through networks quickly. Device isolation also limits breach impacts by ensuring that compromised devices cannot access the entire network.

### Antivirus and Antimalware

The first generation of antivirus software is characterized by signature-based detection and prevention of known viruses. An "A-V" product will now perform generalized malware detection, meaning not just viruses and worms, but also Trojans, spyware, PUPs, cryptojackers, and so on. While A-V software remains important, signature-based detection is widely recognized as insufficient for the prevention of data breaches.

### Disk Encryption

Full disk encryption (FDE) means that the entire contents of the drive (or volume), including system files and folders, are encrypted. OS ACL-based security measures are quite simple to circumvent if an adversary can attach the drive to a different host OS. Drive encryption allays this security concern by making the contents of the drive accessible only in combination with the correct encryption key. Disk encryption can be applied to both hard disk drives (HDDs) and solid state drives (SSDs).

FDE requires the secure storage of the key used to encrypt the drive contents. Normally, this is stored in a Trusted Platform Module (TPM). The TPM chip has a secure storage area to which a disk encryption program, such as Windows BitLocker, can write its keys. It is also possible to use a removable USB drive (if USB is a boot device option). As part of the setup process, you create a recovery password or key. This can be used if the disk is moved to another computer or the TPM is damaged.

![A Screengrab of a window titled, BitLocker Drive Encryption.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/2842-1692974870806.png) Description

The left pane reads control panel home followed by TPM administration, disk management, and privacy statement under the head, see also. The right pane is divided into two sections. The top one is titled, BitLocker Drive Encryption. The text below reads, Help protect your files and folders from unauthorized access by protecting your drives with BitLocker. The bottom one is titled, operating system drive. The link below reads, C colon BitLocker off. A turn BitLocker on link is present on the right.

Activating BitLocker drive encryption. (Screenshot used with permission from Microsoft.)

One of the drawbacks of FDE is that, because the OS performs the cryptographic operations, performance is reduced. This issue is mitigated by self-encrypting drives (SED) , where the cryptographic operations are performed by the drive controller. The SED uses a symmetric data/media encryption key (DEK/MEK) for bulk encryption and stores the DEK securely by encrypting it with an asymmetric key pair called either the authentication key (AK) or Key Encryption Key (KEK). The use of the AK is authenticated by the user password. This means that the user password can be changed without having to decrypt and re-encrypt the drive. Early types of SEDs used proprietary mechanisms, but many vendors now develop using the Opal Storage Specification ([nvmexpress.org/wp-content/uploads/TCGandNVMe_Joint_White_Paper-TCG_Storage_Opal_and_NVMe_FINAL.pdf](https://wmx-api-production.s3.amazonaws.com/courses/54312/supplementary/TCGandNVMe_Joint_White_Paper-TCG_Storage_Opal_and_NVMe_FINAL.pdf#)), developed by the Trusted Computing Group (TCG).

 
|Device|Description|
|---|---|
|Laptops, Desktops, Mobile Devices, and Servers|Full disk encryption ensures that sensitive data is protected even if the storage device is removed from the device or accessed directly using other methods. For virtual machines, FDE prevents direct access to data stored in the virtual machine's disk file.|
|IoT Devices|Internet of Things (IoT) devices, such as smart home devices, wearables, and industrial sensors, often collect and transmit sensitive data. Full disk encryption prevents unauthorized access to this data if the devices are compromised.|
|External Hard Drives and USB Flash Drives, and External Media|Portable storage devices are prone to loss or theft. Full disk encryption ensures that the data stored on these devices remain protected, making it significantly harder for unauthorized individuals to access or retrieve the information.|

### Patch Management

No operating system, software application, or firmware implementation is free from vulnerabilities. As soon as a vulnerability is identified, vendors will try to correct it. At the same time, attackers will try to exploit it. Automated vulnerability scanners can effectively discover missing patches for the operating system plus a wide range of third-party software apps and devices/firmware. Scanning is only useful if effective procedures are in place to apply the missing patches.

In residential and small networks, hosts are typically configured to auto-update, meaning they check for and install patches automatically. The major OS and applications software products are well supported in terms of vendor-supplied fixes for security issues. In Windows, this process is handled by Windows Update, while in Linux, it can be configured via yum-cron or apt unattended-upgrades , depending on the package manager used by the distribution.

Enterprise networks need to be cautious about automated deployment, however, as a patch incompatible with an application or workflow can cause availability issues. In rare cases, such as the infamous SolarWinds hack ([npr.org/2021/04/16/985439655/a-worst-nightmare-cyberattack-the-untold-story-of-the-solarwinds-hack?t=1631031433646](https://www.npr.org/2021/04/16/985439655/a-worst-nightmare-cyberattack-the-untold-story-of-the-solarwinds-hack?t=1631031433646)), update repositories can be infected with malware that can then be spread via automated updates.

There can also be performance and management issues when multiple applications run update clients on the same host. For example, as well as the OS updater, there is likely also a security software update, browser updater, Java updater, OEM driver updater, and so on. These issues can be mitigated by deploying an enterprise patch management suite. Some suites, such as Microsoft’s System Center Configuration Manager (SCCM)/Endpoint Manager ([docs.microsoft.com/en-us/mem/configmgr](https://docs.microsoft.com/en-us/mem/configmgr/)), are vendor specific, while others are designed to support third-party applications and multiple OSes.

Testing patches before deploying them into the production environment is crucial for maintaining the stability and security of software. By conducting thorough testing, organizations can identify potential issues or conflicts arising from the patch, ensuring that it does not introduce new vulnerabilities or disrupt critical operations. Testing helps mitigate the risk of unintended consequences and facilitates a more controlled deployment process, ultimately safeguarding the integrity and reliability of the environment. Testing is typically performed in testing environments built to mirror the production environment as much as appropriate.

Also, it can be difficult to schedule patch operations, especially if applying the patch creates an availability risk to a critical system. If vulnerability assessments continually highlight issues with missing patches, patch management procedures should be upgraded. If the problem affects certain hosts only, it could indicate a compromise that should be investigated more closely.

Patch management can be difficult for legacy systems, proprietary systems, and systems from vendors without robust security management plans, such as some types of Internet of Things devices. These systems will need compensating controls or some other form of risk mitigation if patches are not readily available.