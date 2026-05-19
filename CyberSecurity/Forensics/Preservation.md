It is vital that the evidence collected at the crime scene conform to a valid timeline. Digital information is susceptible to tampering, so access to the evidence must be tightly controlled. Video recording the whole process of evidence acquisition establishes the provenance of the evidence as deriving directly from the crime scene.

To obtain a forensically sound image from nonvolatile storage, the capture tool must not alter data or metadata (properties) on the source disk or file system. Data acquisition would normally proceed by attaching the target device to a forensics workstation or field capture device equipped with a write blocker. A write blocker prevents any data on the disk or volume from being changed by filtering write commands at the driver and OS level.

### Evidence Integrity and Non-Repudiation

Once the target disk has been safely attached to the forensics workstation, data acquisition proceeds as follows:

1. A cryptographic hash of the disk media is made, using either the MD5 or SHA hashing function.
2. A bit-by-bit copy of the media is made using an imaging utility.
3. A second hash is then made of the image, which should match the original hash of the media.
4. A copy is made of the reference image, validated again by the checksum. Analysis is performed on the copy.

This proof of integrity ensures non-repudiation. If the provenance of the evidence is certain, the threat actor identified by analysis of the evidence cannot deny their actions. The hashes prove that no modification has been made to the image.

### Chain of Custody

The host devices and media taken from the crime scene should be labeled, bagged, and sealed, using tamper-evident bags. It is also appropriate to ensure that the bags have antistatic shielding to reduce the possibility that data will be damaged or corrupted on the electronic media by electrostatic discharge (ESD). Each piece of evidence should be documented by a chain of custody form. Chain of custody documentation records where, when, and who collected the evidence, who subsequently handled it, and where it was stored. This establishes the integrity and proper handling of evidence. When security breaches go to trial, the chain of custody protects an organization against accusations that evidence has either been tampered with or is different than it was when it was collected. Every person in the chain who handles evidence must log the methods and tools they used.

The evidence should be stored in a secure facility; this not only means access control, but also environmental control, so that the electronic systems are not damaged by condensation, ESD, fire, and other hazards.