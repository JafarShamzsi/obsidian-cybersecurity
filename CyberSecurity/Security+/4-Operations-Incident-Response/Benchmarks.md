One of the functions of a vulnerability scan is to assess the configuration of security controls and application settings and permissions compared to established benchmarks.

The scanner might try to identify whether there is a lack of controls that might be considered necessary or whether there is any misconfiguration of the system that would make the controls less effective or ineffective, such as antivirus software not being updated, or management passwords left configured to the default. This sort of testing requires specific information about best practices in configuring the particular application or security control. These best practices are provided by listing the controls and appropriate configuration settings in a template.

Security Content Automation Protocol (SCAP) allows compatible scanners to determine whether a computer meets a configuration baseline. SCAP uses several components to accomplish this function, but some of the most important are the following:

- **Open Vulnerability and Assessment Language (OVAL)**—an XML schema for describing system security state and querying vulnerability reports and information.
- **Extensible Configuration Checklist Description Format (XCCDF)**—an XML schema for developing and auditing best practice configuration checklists and rules. Previously, best practice guides might have been written in prose for systems administrators to apply manually. XCCDF provides a machine-readable format that can be applied and validated using compatible software.

![A Screengrab of a window titled, Policy viewer - 513 items.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/7795-1692974874186.png) Description

The Screengrab shows two sections. The top section lists the policy type, policy group or registry key, policy setting, 515 support, and template. The bottom section provides information on policy path, 515 support, and template.

Comparing a local network security policy to a template. The minimum password length set in the local policy is much less than is recommended in the template. (Screenshot used with permission from Microsoft.)

Some scanners measure systems and configuration settings against best practice frameworks. This is referred to as a compliance scan. This might be necessary for regulatory compliance, or you might voluntarily want to conform to externally agreed upon standards of best practice.

![](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/9082-1692974874252.png)

Monitoring template aligned to NIST 800-53 framework requirements.