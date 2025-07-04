Disk image acquisition refers to acquiring data from nonvolatile storage. Nonvolatile storage includes hard disk drives (HDDs), solid state drives (SSDs), firmware, other types of flash memory (USB thumb drives and memory cards), and optical media (CD, DVD, and Blu-ray). This can also be referred to as device acquisition, meaning the SSD storage in a smartphone or media player. Disk acquisition will also capture the OS installation if the boot volume is included.

There are three device states for persistent storage acquisition:

- **Live acquisition**—this means copying the data while the host is still running. This may capture more evidence or more data for analysis and reduce the impact on overall services, but the data on the actual disks will have changed, so this method may not produce legally acceptable evidence. It may also alert the threat actor and allow time for them to perform anti-forensics.
- **Static acquisition by shutting down the host**—this runs the risk that the malware will detect the shutdown process and perform anti-forensics to try to remove traces of itself.
- **Static acquisition by pulling the plug**—this means disconnecting the power at the wall socket (not the hardware power-off button). This is most likely to preserve the storage devices in a forensically clean state, but there is the risk of corrupting data.

Given sufficient time at the scene, an investigator might decide to perform both a live and static acquisition. Whichever method is used, it is imperative to document the steps taken and supply a timeline and video-recorded evidence of actions taken to acquire the evidence.

There are many GUI imaging utilities, including those packaged with forensic suites. If no specialist tool is available, on a Linux host, the dd command makes a copy of an input file (if=) to an output file (of=). In the following, sda is the fixed drive:

dd if=/dev/sda of=/mnt/usbstick/backup.img

A more recent fork of dd is dcfldd, which provides additional features like multiple output files and exact match verification.

![A Screengrab shows few lines of code using dcfldd.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/6009-1692974873000.png)

Using dcfldd (a version of dd with additional forensics functionality created by the DoD) and generating a hash of the source-disk data (sda) .