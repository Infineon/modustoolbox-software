# ModusToolbox Software

As a developer, you have preferred tools and workflows for creating products. ModusToolbox software encompasses a variety of software resources that you can use seamlessly in your existing environment. This page helps you identify and find the ModusToolbox resources available. These resources are grouped in three top-level categories:

- [Tools](#tools)
- [Code Examples](#code-examples)
- [Libraries](#libraries)


## Tools

The ModusToolbox tools package installer (https://www.cypress.com/products/modustoolbox-software-environment) provides various multi-platform development tools to help you work in your preferred flow. The installer includes a make-based build system, Eclipse IDE, configurators, stand-alone project creator and library manager, as well as support for using other IDEs, generating code, compiling, programming, and debugging.

Some tools are available separately on GitHub:

| Tool                                                         | Description                                                  | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Firmware-loader](https://github.com/cypresssemiconductorco/Firmware-loader) | A command-line tool to update KitProg low-level program/debug communication firmware on Cypress kits. Installed with ModusToolbox tools package, newer version may be available on GitHub. | [ReadMe](https://github.com/cypresssemiconductorco/Firmware-loader/blob/master/README.md) |
| [OpenOCD](https://github.com/cypresssemiconductorco/openocd) | The Open On-Chip Debugger provides debugging, in-system programming, and boundary-scan testing. Installed with ModusToolbox tools package, newer version may be available on GitHub. | [ReadMe](https://github.com/cypresssemiconductorco/openocd/blob/cypress/README.MD) |
| [cype](https://github.com/cypresssemiconductorco/cype)       | The Power Estimator (CyPE) library provides software based estimation of power consumption on Cypress kits. This library should be used in conjunction with the Power Estimator tool available in the ModusToolbox version 2.0 of the Eclipsed-base IDE. | [ReadMe](https://github.com/cypresssemiconductorco/cype/blob/master/README.md) |
| [Secure   Boot SDK](https://github.com/cypresssemiconductorco/cysecuretools) | This SDK includes all required libraries, tools, and sample code to provision and develop applications for PSoC 64 MCUs. | [User   Guide](https://www.cypress.com/documentation/software-and-drivers/psoc-64-secure-mcu-secure-boot-sdk-user-guide) |


## Code Examples

Cypress also provides a comprehensive set of code examples covering most -- if not all -- functionality in the provided software. In ModusToolbox, a code example automatically incorporates all libraries required for the application. 

Go to the [ModusToolbox Code Example](https://github.com/cypresssemiconductorco/Code-Examples-for-ModusToolbox-Software) page for a complete list of examples by category.


## Libraries

In addition to the installer and code examples, there are many other parts of ModusToolbox that are provided as libraries. These libraries are essential for taking full advantage of the various features of our PSoC 6 MCUs and Wi-Fi/Bluetooth combo chips. When you create a ModusToolbox application, the system downloads all the libraries your application needs. See the [ModusToolbox Software Overview](https://www.cypress.com/ModusToolboxUserGuide) chapter of the ModusToolbox User Guide to understand how all this works.

From a general perspective, the ModusToolbox libraries include:

- [Board Support Packages](#board-support-packages): For any ModusToolbox application you must specify a BSP, which defines basic device features and capabilities.
- [Board Utils](#board-utils): Different boards have different utilities.
- [PSoC 6 Base Libraries](#psoc-6-base-libraries): There is a set of base libraries that every PSoC 6 application requires.
- [PSoC 6 Feature Libraries](#psoc-6-feature-libraries): There are various additional libraries for the PSoC 6 features.
- [AnyCloud Libraries](#anycloud-libraries): The libraries for AnyCloud applications, enabling Wi-Fi and BT on a PSoC 6 hosted CYW43xxx device.
- [WICED BT SDK Libraries](#wiced-bt-sdk-libraries): The libraries for WICED BT SDK applications, enabling Bluetooth connectivity on stand-alone Bluetooth devices
- [Libraries for Third-Party Systems](#libraries-for-third-party-systems): These libraries are used with third party systems, such as AFR and Mbed OS.

Each library is delivered in its own repository, complete with documentation. The following information includes links to each repository, and various resources associated with each library. Go to each repository to see what releases are available for that library.


#### Board Support Packages

The Board Support Package (BSP) is a central feature of ModusToolbox software. The BSP specifies several critical items for the application, including:

- hardware configuration files for the device (for example, *design.modus*)
- startup code and linker files for the device
- other libraries that are required to support a kit

BSPs are aligned with Cypress kits; they provide files for basic device functionality. A BSP typically has a *design.modus* file that configures clocks and other board-specific capabilities. That file is used by the ModusToolbox configurators. A BSP also includes the required device support code for the device on the board. You can modify the configuration to suit your application. 

Cypress releases BSPs independently of ModusToolbox software as a whole. This [search link](https://github.com/cypresssemiconductorco?q=TARGET_) finds all currently available BSPs on the Cypress GitHub site.

The search results include links to each repository, named TARGET_*kitnumber*. For example, you will find links to repositories like [TARGET_CY8CPROTO-062-4343W](https://github.com/cypresssemiconductorco/TARGET_CY8CPROTO-062-4343W). Each repository provides links to relevant documentation. The following links use this BSP as an example. Each BSP has its own documentation.

The information provided varies, but typically includes one or more of:

- an [API reference for the BSP](https://cypresssemiconductorco.github.io/TARGET_CY8CPROTO-062-4343W/html/modules.html)
- the [BSP Overview](https://cypresssemiconductorco.github.io/TARGET_CY8CPROTO-062-4343W/html/md_bsp_boards_mt_bsp_user_guide.html)
- a link to the [associated kit page](https://www.cypress.com/documentation/development-kitsboards/psoc-6-wi-fi-bt-prototyping-kit-cy8cproto-062-4343w) with kit-specific documentation

A BSP is specific to a board and the device on that board. For custom development, you can create or modify a BSP for your device. See the[ ModusToolbox User Guide](http://www.cypress.com/ModusToolboxUserGuide) chapter on BSPs for how they work and how to create your own for a custom board.


#### Board Utils

Different boards contain different peripherals or utilities (utils for short). The BSP automatically includes the utils libraries for that kit. For example, if the board contains an RGB LED, it will use the rgb-led library. The following show a few of the common utils that may be available for different boards. Your application may include different utils depending on your board's resources.

| Library | Details | Docs |
| ------- | ------- | ---- |
| [CY8CKIT-028-TFT](https://github.com/cypresssemiconductorco/CY8CKIT-028-TFT) | Arduino compatible TFT display that connects to kits such as the [PSoC 6 WiFi-BT Pioneer Kit CY8CKIT-062-WiFi-BT](https://www.cypress.com/cy8ckit-062-wifi-bt). | [Webpage]([CY8CKIT-028-TFT](https://www.cypress.com/documentation/development-kitsboards/tft-display-shield-board-cy8ckit-028-tft)) |
| [retarget-io](https://github.com/cypresssemiconductorco/retarget-io) | Provides a board-independent API to retarget text input/output to a serial UART on a kit | [API   Reference](https://cypresssemiconductorco.github.io/retarget-io/html/index.html) |
| [rgb-led](https://github.com/cypresssemiconductorco/rgb-led) | Provides a board-independent API to use the RGB LED on a kit | [API   Reference](https://cypresssemiconductorco.github.io/rgb-led/html/index.html) |
| [serial-flash](https://github.com/cypresssemiconductorco/serial-flash) | Provides a board-independent API to use the serial flash on a kit | [API   Reference](https://cypresssemiconductorco.github.io/serial-flash/html/index.html) |


#### 


#### PSoC 6 Base Libraries

A BSP uses low-level resources to add functionality. For example, a PSoC 6 BSP typically adds the following libraries, as appropriate for the kit/device:

| Library                                                      | Details                                                      | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [abstraction-rtos](https://github.com/cypresssemiconductorco/abstraction-rtos) | Abstraction layers provide APIs that allow different libraries to interact with each other without having to know specific details about a given library. This library provides a common API that allows code or middleware to use RTOS features. In the ModusToolbox Library Manager, this library is listed under "Abstraction Layer." | [API   Reference](https://cypresssemiconductorco.github.io/abstraction-rtos/html/index.html) |
| [core-lib](https://github.com/cypresssemiconductorco/core-lib) | Header files that declare basic types and utilities (such as result types or ASSERT) that can be used by multiple BSPs. | [API   Reference](https://cypresssemiconductorco.github.io/core-lib/html/index.html) |
| [psoc6cm0p](https://github.com/cypresssemiconductorco/psoc6cm0p) | Prebuilt application images for the Cortex M0+ CPU of a dual-CPU PSoC 6 device. | Repository [readme file](https://github.com/cypresssemiconductorco/psoc6cm0p/blob/master/README.md) |
| [psoc6hal](https://github.com/cypresssemiconductorco/psoc6hal) | The Hardware Abstraction Layer (HAL) provides a high-level interface to configure and use hardware blocks on Cypress MCUs. It is a generic interface that can be used across multiple product families. The focus on ease-of-use and portability means the HAL does not expose all of the low-level peripheral functionality | [API   Reference](https://cypresssemiconductorco.github.io/psoc6hal/html/index.html) |
| [psoc6make](https://github.com/cypresssemiconductorco/psoc6make) | The build recipe makefiles and scripts for building and programming PSoC 6 applications. You can build an application either through a command-line interface (CLI), the ModusToolbox IDE, or a third-party IDE. | Repository [readme file](https://github.com/cypresssemiconductorco/psoc6make/blob/master/README.md) |
| [psoc6pdl](https://github.com/cypresssemiconductorco/psoc6pdl) | Peripheral driver library for PSoC 6 devices. The library is device-independent, so it can be precompiled and used for any PSoC 6 MCU device or project. Included automatically by any BSP targeting a PSoC 6 device | [API   Reference](https://cypresssemiconductorco.github.io/psoc6pdl/pdl_api_reference_manual/html/index.html) |
| [abstraction-rtos](https://github.com/cypresssemiconductorco/abstraction-rtos) | Abstraction layers provide APIs that allow different libraries to interact with each other without having to know specific details about a given library. A common API that allows code or middleware to use RTOS features without knowing what the RTOS is | [API   Reference](https://cypresssemiconductorco.github.io/abstraction-rtos/html/index.html) |


#### PSoC 6 Feature Libraries
PSoC 6 feature libraries (also called middleware), provide access to various features on the device, including:

| Library                                                      | Details                                                      | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [bless](https://github.com/cypresssemiconductorco/bless)     | This library is specific to devices like **CY8C6347BZI-BLD53**, with onboard Bluetooth and no separate connectivity device. The Bluetooth Low Energy Subsystem (bless) library contains a comprehensive API to configure the BLE Stack and the underlying chip hardware. | [API   Reference](https://cypresssemiconductorco.github.io/bless/ble_api_reference_manual/html/index.html) |
| [capsense](https://github.com/cypresssemiconductorco/capsense) | Capacitive sensing can be used in a variety of applications and products where conventional mechanical buttons can be replaced with sleek human interfaces to transform the way users interact with electronic systems. | [API   Reference](https://cypresssemiconductorco.github.io/capsense/capsense_api_reference_manual/html/index.html) |
| [clib-support](https://github.com/cypresssemiconductorco/clib-support) | The CLib FreeRTOS Support Library provides the necessary hooks to make C library functions such as malloc and free thread safe. | [API Reference](https://cypresssemiconductorco.github.io/clib-support/html/index.html) |
| [csdadc](https://github.com/cypresssemiconductorco/csdadc)   | Enables the ADC functionality of the CapSense Sigma-Delta (CSD) hardware block. Useful for devices that do not include other ADC/IDAC options. | [API   Reference](https://cypresssemiconductorco.github.io/csdadc/csdadc_api_reference_manual/html/index.html) |
| [csdidac](https://github.com/cypresssemiconductorco/csdidac) | The same, for IDAC functionality.                            | [API   Reference](https://cypresssemiconductorco.github.io/csdidac/csdidac_api_reference_manual/html/index.html) |
| [dfu](https://github.com/cypresssemiconductorco/dfu)         | The Device Firmware Update (DFU) library provides an API for updating firmware images. | [API   Reference](https://cypresssemiconductorco.github.io/dfu/dfu_sdk_api_reference_manual/html/index.html) |
| [emeeprom](https://github.com/cypresssemiconductorco/emeeprom) | The Emulated EEPROM library provides an API to manage an emulated EEPROM in flash. It has support for wear leveling and restoring corrupted data from a redundant copy. | [API   Reference](https://cypresssemiconductorco.github.io/emeeprom/em_eeprom_api_reference_manual/html/index.html) |
| [emwin](https://github.com/cypresssemiconductorco/emwin)     | SEGGER embedded graphic library and graphical user interface (GUI)   framework designed to provide processor- and display controller-independent GUI for any application that needs a graphical display. | [Overview](https://cypresssemiconductorco.github.io/middleware-emwin/emwin_overview/html/index.html) |
| [freertos](https://github.com/cypresssemiconductorco/freertos) | FreeRTOS kernel, distributed as standard C source files with   configuration header file, for use with the PSoC 6 MCU. | [FreeRTOS web page](http://www.freertos.org/a00106.html)     |
| [usbdev](https://github.com/cypresssemiconductorco/usbdev)   | The USB Device library provides a full-speed USB 2.0 Chapter 9   specification compliant device framework. | [API   Reference](https://cypresssemiconductorco.github.io/usbdev/usbfs_dev_api_reference_manual/html/index.html) |


#### AnyCloud Libraries

AnyCloud is based on the industry standard lwIP TCP/IP stack and Mbed TLS network security. These libraries provide core functionality including connectivity, security, firmware upgrade support, and application layer protocols for applications that do not use commercial cloud management systems.

| Library | Description | Docs |
| ------- | ----------- | ---- |
| [wifi-mw-core](https://github.com/cypresssemiconductorco/wifi-mw-core) | The Wi-Fi Middleware Core library bundles the core libraries that any Wi-Fi application needs. | [API Reference](https://cypresssemiconductorco.github.io/wifi-mw-core/api_reference_manual/html/index.html) |
| [wifi-connection-manager](https://github.com/cypresssemiconductorco/wifi-connection-manager) | The Wi-Fi Connection Manager (WCM) includes the wifi-mw-core library by default and provides easy to use APIs to establish and monitor Wi-Fi connections on Cypress devices that support Wi-Fi connectivity. | [API Reference](https://cypresssemiconductorco.github.io/wifi-connection-manager/api_reference_manual/html/index.html) |
| [wifi-host-driver](https://github.com/cypresssemiconductorco/wifi-host-driver) | The Wi-Fi Host Driver (WHD) is an independent, embedded driver that provides a set of APIs to interact with Cypress WLAN chips. | [API Reference](https://cypresssemiconductorco.github.io/wifi-host-driver/API/index.html) |
| [anycloud-ota](https://github.com/cypresssemiconductorco/anycloud-ota) | This Over-The-Air (OTA) library enables applications to implement sophisticated OTA software updates from any cloud platform using custom cloud management tools. | [API Reference](https://cypresssemiconductorco.github.io/anycould-ota/api_reference_manual/html/index.html) |
| [mqtt](https://github.com/cypresssemiconductorco/mqtt) | This library includes the open source AWS IoT device SDK embedded C library plus some glue to ensure seamless MQTT cloud connectivity. | [API Reference](https://cypresssemiconductorco.github.io/mqtt/api_reference_manual/html/index.html) |
| [secure-sockets](https://github.com/cypresssemiconductorco/secure-sockets) | The Secure Sockets library eases application development by exposing a socket like interface for both secure and non-secure socket communication. | [API Reference](https://cypresssemiconductorco.github.io/secure-sockets/api_reference_manual/html/index.html) |
| lwIP | This is a lightweight open-source TCP/IP stack. | [Non-Cypress website](http://www.nongnu.org/lwip/2_1_x/index.html) |
| [cy-mbedtls-acceleration](https://github.com/cypresssemiconductorco/cy-mbedtls-acceleration) | Cypress provides a library that extends MbedTLS to enable hardware-accelerated encryption on PSoC 6 devices. | [Arm Mbed TLS](https://github.com/ARMmbed/mbedtls) |
| [lpa](https://github.com/cypresssemiconductorco/lpa) | The Low Power Assistant (LPA) is a library and associated settings in the ModusToolbox Device Configurator that allow you to configure a PSoC 6 Host and WLAN (Wi-Fi / BT Radio) device for optimized low-power operation. | [API Reference](https://cypresssemiconductorco.github.io/lpa/lpa_api_reference_manual/html/index.html) |
| Bluetooth Libraries | With these libraries, you can use the Bluetooth LE functionality in the 43xxx combo device to enable BLE for your device. | [bluetooth-freertos](https://github.com/cypresssemiconductorco/bluetooth-freertos) and [btstack](https://github.com/cypresssemiconductorco/btstack) |
| [connectivity-utilities](https://github.com/cypresssemiconductorco/connectivity-utilities) | General purpose middleware connectivity utilities, for instance a   linked_list or a json_parser. This library is supported on both AnyCloud and Mbed OS. | See the code for each |


#### WICED BT SDK Libraries

In the ModusToolbox environment, create the "wiced_btsdk" code example first. That creates a local instance of the entire SDK on your computer. Follow the instructions in the the Project Creator tool. For more details about the WICED BT SDK, refer to https://cypresssemiconductorco.github.io/btsdk-docs/BT-SDK/index.html.

The Bluetooth SDK is factored into a collection of smaller libraries, so that you can download and use those parts of the SDK necessary for your application. If you use a code example, you don't need to download or install individual libraries. 

The SDK features a dual-mode Bluetooth stack with stack- and profile-level APIs for embedded BT application development. It supports GAP,  GATT, SMP, RFCOMM, SDP, AVDT/AVCT and BLE Mesh protocols, as well as over-the-air upgrade.

- [btsdk-audio](https://github.com/cypresssemiconductorco/btsdk-audio) 
- [btsdk-ble](https://github.com/cypresssemiconductorco/btsdk-ble) 
- [btsdk_drivers](https://github.com/cypresssemiconductorco/btsdk-drivers) 
- [btsdk-hid](https://github.com/cypresssemiconductorco/btsdk-hid) 
- [btsdk-include](https://github.com/cypresssemiconductorco/btsdk-include) 
- [btsdk-mesh](https://github.com/cypresssemiconductorco/btsdk-mesh) 
- [btsdk-ota](https://github.com/cypresssemiconductorco/btsdk-ota) 
- [btsdk-rfcomm](https://github.com/cypresssemiconductorco/btsdk-rfcomm) 
- [btsdk-tools](https://github.com/cypresssemiconductorco/btsdk-tools) 
- [btsdk-utils](https://github.com/cypresssemiconductorco/btsdk-utils) 
- [btsdk-host-apps-bt-ble](https://github.com/cypresssemiconductorco/btsdk-host-apps-bt-ble) 
- [btsdk-host-apps-mesh](https://github.com/cypresssemiconductorco/btsdk-host-apps-mesh) 
- [btsdk-peer-apps-bel](https://github.com/cypresssemiconductorco/btsdk-peer-apps-ble) 
- [btsdk-peer-apps-mesh](https://github.com/cypresssemiconductorco/btsdk-peer-apps-mesh) 
- [btsdk-peer-apps-ota](https://github.com/cypresssemiconductorco/btsdk-peer-apps-ota) 



#### Libraries for Third-Party Systems

ModusToolbox supports some third-party IoT ecosystems, like AWS IoT. Vendors typically provide libraries for their ecosystem. Cypress extends some vendors' libraries to provide support for our devices (like aws-iot), provides a utility to make working with an ecosystem library easier (like http-server), and uses some open source libraries as they are (like Arm MBed TLS).

| Library                                                      | Details                                                      | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [aws-iot](https://github.com/cypresssemiconductorco/aws-iot) | Provides secure, bi-directional communication between Internet-connected devices such as sensors, actuators, embedded micro-controllers, or smart appliances and the AWS Cloud. Supports MQTT and HTTP protocols. | [Developer   Guide](https://docs.aws.amazon.com/iot/latest/developerguide/what-is-aws-iot.html) |
| [enterprise-security](https://github.com/cypresssemiconductorco/enterprise-security) | This library implements a collection of the most commonly used   Extensible Authentication Protocols (EAP) used in enterprise WiFi networks | [API   Reference](https://cypresssemiconductorco.github.io/enterprise-security/api_reference_manual/html/index.html) |
| [http-server](https://github.com/cypresssemiconductorco/http-server) | Provides communication functions for an HTTP server.         | [ReadMe](https://github.com/cypresssemiconductorco/http-server/blob/master/README.md) |
| [connectivity-utilities](https://github.com/cypresssemiconductorco/connectivity-utilities) | General purpose middleware connectivity utilities, for instance a   linked_list or a json_parser. This library is supported on both AnyCloud and Mbed OS. | See the code for each                                        |
| Mbed OS HAL                                                  | Mbed’s hardware abstraction layer. Support for Cypress targets is available from the Mbed OS archive. This HAL is part of the Mbed ecosystem and not provided directly by Cypress. | [Mbed API documentation](https://os.mbed.com/docs/mbed-os/v5.13/apis/index.html) |
| Arm Mbed TLS                                                 | A library to include cryptographic and SSL/TLS capabilities in an embedded application. It is part of the Mbed OS ecosystem and not provided by Cypress. | [API Reference](https://tls.mbed.org/api/)                   |



© Cypress Semiconductor Corporation, 2020. This document is the property of Cypress Semiconductor Corporation and its subsidiaries ("Cypress"). 
