---
title: "Payment Card Industry security guidance for app developers"
slug: "pci-security-guidance-for-app-developers"
excerpt: ""
hidden: false
metadata: 
  description: "Clover devices operate on a custom version of the Android operating system. To develop apps for Clover devices, you need to ensure compatibility with the Android OS. Use the PCI DSS checklist for developers to get started with the data security standards and resources for safe payments using your apps on Clover devices."
  image: []
  robots: "index"
createdAt: "Wed Apr 17 2024 04:03:23 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri May 10 2024 22:23:09 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<!--DDS-6146 New topic-->\n<meta name=\"description\" content=\"Clover devices run a custom version of the Android operating system. Clover devices operate on a custom version of the Android operating system. To develop apps for Clover devices, you need to ensure compatibility with the Android OS. Use the PCI DSS checklist for developers to get started with the data security standards and resources for safe payments using your apps on Clover devices.. Use the PCI DSS checklist for developers to get started with the data security standards and resources for safe payments using your apps on Clover devices.\">"
}
[/block]


[block:html]{"html":"<div class=\"container-top\">\n  <!--United States-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">United States</div>\n    </div>\n  </div>\n  \n  <!--Canada-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Canada</div>\n    </div>\n  </div>\n\n  <!--Europe-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Europe</div>\n    </div>\n  </div>\n\n  <!--Latin America-->\n  <div class=\"container-reg\">\n    <div class=\"pill-reg\">\n      <div class=\"label-reg\">Latin America</div>\n    </div>\n  </div>\n</div>\n\n\n<!--Css-->\n<style>\n.container-top {\n  top: -15px;\n  position: relative;\n  margin-bottom: -5px;\n}\n\n.container-reg {\n  align-items: center;\n  min-width: auto; \n  width: fit-content;\n  text-align: left;\n  overflow: auto;\n  display: inline-block; \n}\n\n/*Pill format REG*/\n.pill-reg {\n  background: #44BB44;\n  border: .5px solid #44BB44;\n  margin-left: 5px;\n  overflow: auto;\n  display: flex; \n  justify-content: center; \n  align-items: center; \n  border-radius: 10px;\n  height: 1.8rem;\n  margin-top: 10px;\n  margin-bottom: 1.5px; \n  padding: 0 10px; \n}\n\n/*Text FORMAT inside REG pills */\n.pill-reg .label-reg, \n.pill-reg__addon .label-reg \n{\n  font-style: normal;\n  font-weight: normal;\n  font-size: 12px;\n  color: #fff;\n  vertical-align: middle;\n  margin: 0;\n  padding: 0 5px;\n}\n</style>"}[/block]

# What is PCI DSS

Payment Card Industry Data Security Standard (PCI DSS) includes a wide range of security controls in the handling of card data and payment information. These controls cover aspects such as system configuration, policies, procedures, and permissions related to cardholder data. Secure software development and effective management play a crucial role in achieving PCI compliance.

PCI standards apply to various entities involved in payment card processing, regardless of their size or transaction volume. These include—card readers (both physical and virtual), point of sale devices, store networks and wireless access routers, payment card data storage and transmission (both electronic and paper),  E-commerce platforms, online payment gateways, and shopping carts. 

For more information, see [What is PCI compliance? The All-You-Need-to-Know Guide](https://www.clover.com/ca/small-business-resources/pci-compliance).

> 📘 PCI DSS v4.0
> 
> PCI DSS v4.0 replaced v3.2.1 on March 31, 2024, and PCI DSS v4.0 documents are available for compliance assessment. Always see the information available in the [PCI Security Standards Council document library](https://www.pcisecuritystandards.org/document_library/?category=pcidss&hsCtaTracking=8aa4514c-37d0-40bc-b864-ed4c4aebb5de%7C8d5a5e5f-7860-4a8c-97cc-d91f17654660).

# Guidance for developers

For developers, the scope of PCI includes three key concepts:

- **Minimize data storage**—Keep as little customer data as necessary to minimize security risks.
- **Secure data handling**—Implement strong security measures for data both when stored and during transmission.
- **Vulnerability protection**—Make sure that information systems and software are protected from malicious attacks.

***

# PCI DSS checklist for developers

Clover devices run a custom version of the Android operating system (OS), so your apps need to be compatible with the Android OS. The following checklist can help you get started with the data security standards and resources for safe payments using your apps on Clover devices.

[block:html]
{
  "html": "<!--BEGIN list-->\n    <details>\n     \n        <Summary>In this section</Summary>\n        <article>\n          <p class=\"toc1\"><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#1-hardware-interfaces\">1. Hardware interfaces</a></p>\n        <ul>\n            <li><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#11-ethernet-interface-security-considerations\">1.1 Ethernet interface security considerations</a></li>\n            <li><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#12-wi-fi-interface-security-guidelines\">1.2 Wi-Fi interface security guidelines </a></li>\n <li><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#13-lte-interface-security-guidelines\">1.3 LTE interface security guidelines </a></li>\n  <li><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#14-usb-interface-security-guidelines\">1.4 USB interface security guidelines</a></li>\n            <li><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#15-nfc-contactless\">1.5 NFC contactless </a></li>\n <li><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#16-spi\">1.6 SPI</a></li>\n <li><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#17-uart\">1.7 UART</a></li>\n\n        </ul>\n <p class=\"toc1\"><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#2--protocols\">2. Protocols</a></p>\n        <ul>\n            <li><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#21-tcpip\"> 2.1 TCP/IP </a></li>\n <li><a href=\"https://docs.clover.com/docs/pci-security-guidance-for-app-developers#22-bluetooth\"> 2.2 Bluetooth </a></li>\n</ul>\n        </article>\n    </details>\n<!--END list-->\n\n<hr />\n<style>\ndetails {\n  padding: 5px 10px 5px 30px;\n  background-color: #EDEDED;\n  border-radius: 5px;\n\tborder: 1px solid #228800;*/\n  }\nsummary {\n  list-style-position: outside;\n  margin-left: 5px;\n  padding: 3px 10px 10px 20px;\n  border-radius: 5px;\n /* background-color: #F9F9F9;*/\n  color: #228800;\n  font-size:1.3em;\n  /*font-weight: 600;*/\n}\nsummary::marker {\n    color: #228800;\n    font-size: 1.3em;\n  }\narticle {\n    margin-left: 30px;\n  }\np.toc1 {\n  color: #228800;\n  font-weight:500;\n  font-size: 1em;\n  margin:8px 0px 3px 0px;\n  }\n    \n</style>\n</details>"
}
[/block]


<br>

# 1\. Hardware interfaces

Hardware interfaces play a crucial role in connecting software applications to external devices and networks. You need to be aware of security considerations related to Ethernet, Wi-Fi connections, LTE and USB connections, and more.

## 1.1 Ethernet interface security considerations

When working with the <<glossary:Ethernet>> interface, developers must prioritize security and stability. Android does not provide direct access to low-level Ethernet details due to these considerations.

1. Get network permissions
   - [ ] Request necessary permissions in your app's manifest file to access the Ethernet interface.
   - [ ] Use the `android.permission.INTERNET` permission to enable network communication.
2. Use secure network protocols
   - [ ] Use secure HTTP (HTTPS) to encrypt data in transit and prevent eavesdropping and man-in-the-middle attacks.
   - [ ] Use TLS v1.2+ for secure connections. Plain HTTP is not allowed for Ethernet communication.
3. Network security configuration
   - [ ] Use the Android Network Security Configuration feature.
   - [ ] Define security policies for network connections, including trusted certificate authorities and enforced secure communication protocols.
   - [ ] Validate server certificates for the authenticity and integrity of servers before establishing connections.
4. Connection management
   - [ ] Manage connections to prevent security risks such as connection hijacking and denial-of-service attacks.
   - [ ] Close connections when no longer needed and handle connection errors gracefully.
5. Leverage third-party libraries and APIs
   - [ ] Exercise caution when integrating third-party libraries for network access.
   - [ ] Assess security practices and potential vulnerabilities of third-party libraries.
   - [ ] Use official Android APIs, such as `ConnectivityManager` and `WifiManager.` These APIs provide controlled access and data sandboxing for secure network management.
6. Respect user privacy
   - [ ] Ensure data collected through the network aligns with your app's purpose and adheres to user privacy regulations.
7. Follow secure coding practices
   - [ ] Implement secure coding techniques such as input validation, memory management, and proper permissions handling to avoid potential vulnerabilities.
8. Regularly update your app
   - [ ] Patch known security flaws promptly.
   - [ ] Address emerging threats by keeping your app and its dependencies updated.

[Back to top](https://docs.clover.com/docs/pci-security-guidance-for-app-developers#pci-dss-checklist-for-developers)

***

## 1.2 Wi-Fi interface security guidelines

When dealing with Wi-Fi connectivity on Clover devices, consider the following security practices:

1. Secure connection management
   - [ ] Prioritize secure Wi-Fi connections to prevent unauthorized access.
   - [ ] Note that Clover device firmware prohibits connecting to access points using Wired Equivalent Privacy (WEP) or without encryption.
   - [ ] Turn off unnecessary features, such as Wi-Fi Protected Setup (WPS) and Universal Plug and Play (UPnP).
   - [ ] Prevent unauthorized network discovery by disabling service set identifier (SSID) broadcasting.
2. Implement strong password requirements
   - [ ] Encourage users to create strong and unique Wi-Fi passwords.
   - [ ] Provide guidance on password strength and security.
3. Avoid unnecessary network scans
   - [ ] Excessive scanning for Wi-Fi networks can drain device battery and reveal unnecessary information.
   - [ ] Optimize network scans to balance functionality and efficiency.
4. Leverage official APIs
   - [ ] Use official Android APIs and frameworks for secure Wi-Fi access.
   - [ ] Maintain managed Wi-Fi connections within the Android framework.
5. Network Access Control (NAC)
   - [ ] Authenticate and authorize devices connecting to Wi-Fi networks.
   - [ ] Implement methods, such as MAC address filtering or 802.1X authentication, to enforce security policies.
6. Create user awareness
   - [ ] Educate users about Wi-Fi security best practices:
   - [ ] Avoid connecting to public or unsecured Wi-Fi networks.
   - [ ] Use VPNs when accessing sensitive data over Wi-Fi.
   - [ ] Provide guidance on secure Wi-Fi settings configuration.

[Back to top](https://docs.clover.com/docs/pci-security-guidance-for-app-developers#pci-dss-checklist-for-developers)

***

## 1.3 LTE interface security guidelines

Due to security and stability considerations, Android does not directly expose the low-level details of the <<glossary:LTE>> interface. Some security considerations for developers interacting with mobile data are:

1. Prioritize user privacy and security
   - [ ] Protect user data and device security when interacting with mobile data networks.
   - [ ] Get prior user consent for high data usage if your app significantly increases mobile data usage.
   - [ ] Ensure data collected through the mobile data aligns with your app's purpose and adheres to user privacy regulations. 
   - [ ] Track and inform users about their mobile data usage within your app.
2. Use secure network protocols
   - [ ] Use secure HTTP (HTTPS) to encrypt data in transit and prevent eavesdropping and man-in-the-middle attacks.
   - [ ] Use TLS v1.2+ for secure connections. Plain HTTP is not allowed.
3. Validate server certificates
   - [ ] Verify the authenticity and integrity of servers before establishing connections.
4. Leverage third-party libraries and APIs
   - [ ] Exercise caution when integrating third-party libraries for network access.
   - [ ] Assess security practices and potential vulnerabilities of third-party libraries.
   - [ ] Use official Android APIs, such as `ConnectivityManager` and `WifiManager` when direct access to the LTE interface isn't available. These APIs provide controlled access and data sandboxing for secure network management.
5. Secure data collection and handling
   - [ ] Use strong encryption algorithms and key management practices to protect sensitive information, such as user credentials and financial data.
   - [ ] Avoid hardcoding sensitive data. Store sensitive data securely in the Android Keystore or other appropriate mechanisms.
   - [ ] Limit access to sensitive data based on the principle of least privilege.
   - [ ] Use static and dynamic analysis tools to identify potential security issues related to mobile data communication.
   - [ ] Prevent injection attacks by properly validating and sanitizing user input before processing.
6. Avoid bypassing security restrictions
   - [ ] Refrain from bypassing Android's built-in security measures for mobile data access. Bypassing security restrictions can compromise security and stability.
7. Follow secure coding practices
   - [ ] Implement secure coding techniques such as avoiding buffer overflows, proper memory management, and secure network socket handling to avoid vulnerabilities in your code.
8. Regularly update your app
   - [ ] Patch known security flaws promptly.
   - [ ] Address emerging threats by keeping your app and its dependencies updated.
   - [ ] Keep yourself updated on security threats and vulnerabilities related to mobile data networks and Android development.

[Back to top](https://docs.clover.com/docs/pci-security-guidance-for-app-developers#pci-dss-checklist-for-developers)

***

## 1.4 USB interface security guidelines

When dealing with <<glossary:USB>> connectivity, it's important to prioritize user privacy and device security. For more information, see [USB host and accessory overview](https://developer.android.com/develop/connectivity/usb). Key considerations for developers working with USB devices include:

1. Prioritize user privacy and security
   - [ ] Implement the `UsbManager.requestPermission` method to explicitly ask for user consent before accessing any USB device.
   - [ ] Respect the user's decision if they deny permission to access the USB device.
   - [ ] Inform users clearly why your app needs USB access and what data it intends to read or write. Transparency builds trust and ensures informed consent.
   - [ ] Take necessary measures to protect user data and device security when interacting with USB devices.
2. Verify the identity and compatibility of connected devices
   - [ ] Implement mechanisms to verify the identity of connected USB devices.
   - [ ] Verify vendor and product IDs, serial numbers, or other device-specific information to make sure only trusted devices are accessed.
   - [ ] Ensure your app supports specific USB device hardware and firmware versions it may encounter.
   - [ ] Implement proper error handling to address scenarios where the USB device isn't connected, malfunctions, or requires specific drivers.
3. Secure data collection and handling
   - [ ] Limit access to USB devices to what your app requires to reduce potential security risks.
   - [ ] Collect only the necessary data from the USB device for your app's functionality. Avoid unnecessary data retrieval to reduce exposure.
   - [ ] Prevent injection attacks by properly validating and sanitizing data from a USB device before processing.
   - [ ] Encrypt sensitive data in both transit and at rest with strong encryption algorithms and secure key management practices.
   - [ ] Use static and dynamic analysis tools to identify potential security issues related to USB data communication.
4. Leverage official APIs
   - [ ] Use the official `UsbManager` and related APIs for secure and managed USB communication within the Android framework.
   - [ ] Refrain from bypassing official APIs or directly accessing low-level USB protocols. Custom implementations can compromise security and stability.
5. Follow secure coding practices
   - [ ] Implement secure coding techniques such as avoiding buffer overflows, proper memory management, and secure network socket handling to avoid vulnerabilities in your code.
   - [ ] Regularly update your app to patch known vulnerabilities and address emerging security threats related to USB interfaces.

[Back to top](https://docs.clover.com/docs/pci-security-guidance-for-app-developers#pci-dss-checklist-for-developers)

***

## 1.5 NFC contactless

The near-field communication (<<NFC>>) hardware is connected only to the secure processor. The application processor running Android has no access to the NFC hardware.

For more information, see [Near field communication (NFC) overview](https://developer.android.com/develop/connectivity/nfc). 

***

## 1.6 SPI

The Serial Peripheral Interface (SPI) connection between secure and application processors is not accessible by application developers.

***

## 1.7 UART

The Universal Asynchronous Receiver-Transmitter (<<glossary:UART>>) connection between secure and application processors is not exposed to application developers.

[Back to top](https://docs.clover.com/docs/pci-security-guidance-for-app-developers#pci-dss-checklist-for-developers)

***

# 2\.  Protocols

## 2.1 TCP/IP

Using TCP/IP networking securely is important for building robust and efficient network-connected applications. Key security guidance points include:

1. Use secure network protocols
   - [ ] Use secure HTTP (HTTPS) and TLS/SSL for sockets to encrypt data in transit and prevent eavesdropping and man-in-the-middle attacks.
   - [ ] Use protocols with strong security features, such as TLS 1.2+, and avoid plain HTTP.
2. Network security configuration
   - [ ] Use the Android Network Security Configuration feature.
   - [ ] Define security policies for network connections, including trusted certificate authorities and enforced secure communication protocols.
   - [ ] Validate server certificates for the authenticity and integrity of servers before establishing connections.
   - [ ] Implement proper error handling to manage connection failures, disconnections, and potential security issues.
3. Use secure libraries and APIs
   - [ ] Use libraries with a proven track record of security updates and adherence to best practices.
   - [ ] Use secure Android networking APIs, such as `URLConnection`, `Socket`, and `HttpClient` for managed network communication.
4. Secure data collection and handling
   - [ ] Collect only the necessary data for your app's functionality. Avoid unnecessary data retrieval to reduce exposure.
   - [ ] Encrypt sensitive data with strong encryption algorithms such as AES-256 and secure key management for sensitive data, such as user credentials and financial information.
   - [ ] Validate all input received from TCP/IP connections to prevent common security vulnerabilities such as injection attacks and buffer overflows. 
   - [ ] Sanitize input data to mitigate the risk of malicious input that could lead to security breaches.
5. Follow secure coding practices
   - [ ] Implement secure coding techniques such as input validation, memory management, and proper permissions handling to avoid vulnerabilities in your code.
6. Run regular security updates
   - [ ] Keep TCP/IP software components updated with security patches to address known vulnerabilities and improve security features.
   - [ ] Regularly check for updates provided by software vendors and apply them promptly.
7. Secure socket handling
   - [ ] Implement proper socket handling practices to prevent security vulnerabilities such as socket hijacking or connection tampering. 
   - [ ] Close sockets when not needed and handle socket errors properly to prevent security incidents.

[Back to top](https://docs.clover.com/docs/pci-security-guidance-for-app-developers#pci-dss-checklist-for-developers)

***

## 2.2 Bluetooth

Bluetooth, both as a hardware interface and protocol, plays a significant role in wireless communication. To enhance security, consider the following guidance points:

1. Prioritize user privacy and security
   - [ ] Request necessary permissions from users. Clearly explain why your app needs Bluetooth access and request appropriate permissions, for example, BLUETOOTH and BLUETOOTH_ADMIN, through the manifest file.
   - [ ] Inform users about the Bluetooth devices your app intends to connect to and get their explicit consent before establishing connections. Avoid pre-pairing or automatic connections without user approval.
2. Enforce secure pairing and bonding
   - [ ] Enforce secure pairing: Always use secure pairing mechanisms to authenticate and encrypt communication during pairing. Never rely on legacy pairing methods.
   - [ ] Use appropriate bonding. Implement proper checks to verify the identity of the Bluetooth device you're connecting to before establishing a connection.
3. Secure data collection and handling
   - [ ] Collect only the necessary data for your app's functionality and avoid unnecessary transfer over Bluetooth.
   - [ ] Encrypt data in transit. Use Secure Bluetooth (SPP) or GATT profiles that use encryption and authentication for secure data transmission. Never send sensitive data, such as passwords or credentials, over Bluetooth without encryption.
   - [ ] Encrypt data at rest. If Bluetooth data is stored on the device, make sure it is encrypted with strong algorithms, such as AES-256, and securely stored using Android Keystore or similar mechanisms.
4. Connection management
   - [ ] Avoid unnecessary scans: Scan for Bluetooth devices only when your app requires it and optimize scanning duration to minimize energy consumption and potential for discovery by unintended recipients.
   - [ ] Handle connections properly: Implement proper error handling and security checks during device discovery, pairing, connection establishment, and data transfer.
5. Leverage official APIs
   - [ ] Leverage well-tested and secure Android Bluetooth APIs, such as `BluetoothAdapter`, `BluetoothDevice`, `Gatt`, and `GattCallback` for managing Bluetooth interactions.
6. Follow secure coding practices
   - [ ] Implement secure coding techniques such as input validation, memory management, and proper permissions handling to avoid vulnerabilities in your code. Your choice of language may impact these practices; for example, native code requires more vigilance against memory mismanagement than Java.
7. Beware of Bluetooth Low Energy (BLE) vulnerabilities
   - [ ] Understand potential vulnerabilities, such as relay attacks, man-in-the-middle attacks, and service discovery vulnerabilities. Implement mitigation strategies, such as secure pairing, encryption, and access control mechanisms.
   - [ ] Refrain from bypassing Android Bluetooth security mechanisms. Use APIs and protocols to ensure secure interactions. Avoid attempts to directly access low-level Bluetooth functionality, which can compromise security.
8. Stay informed
   - [ ] Keep yourself updated on security threats and vulnerabilities related to Bluetooth protocols and Android development.

[Back to top](https://docs.clover.com/docs/pci-security-guidance-for-app-developers#pci-dss-checklist-for-developers)
