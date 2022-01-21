# ModusToolbox™ software

ModusToolbox™ software is a modern, extensible development environment supporting a wide range of Infineon microcontroller devices. It provides a flexible set of tools and a diverse, high-quality collection of application-focused software. These include configuration tools, low-level drivers, libraries, and operating system support, most of which are compatible with Linux, macOS, and Windows-hosted environments. 

This page helps you identify and find the ModusToolbox™ resources available. These resources are grouped in the following top-level categories:

- [Tools](#tools)
- [Code examples](https://github.com/Infineon/Code-Examples-for-ModusToolbox-Software) (link to separate page)
- [Board support packages](#board-support-packages)
- [Libraries](#libraries)
- [Training material](https://github.com/Infineon/training-modustoolbox) (link to separate page)

## Tools

The ModusToolbox™ tools package installer (https://www.cypress.com/products/modustoolbox-software-environment) provides various multi-platform development tools to help you work in your preferred flow. The installer includes a make-based build system, Eclipse IDE, configurators, stand-alone project creator and library manager, as well as support for using other IDEs, generating code, compiling, programming, and debugging. Refer to the [ModusToolbox™ user guide](https://www.cypress.com/ModusToolboxUserGuide) for complete details.

Some tools are available separately on GitHub:

| Tool                                                         | Description                                                  | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Firmware-loader](https://github.com/Infineon/Firmware-loader) | A command-line tool to update KitProg low-level program/debug communication firmware on Cypress kits. Installed with ModusToolbox™ tools package, newer version may be available on GitHub. | [readme](https://github.com/Infineon/Firmware-loader/blob/master/README.md) |
| [OpenOCD](https://github.com/Infineon/openocd)               | The Open On-Chip Debugger provides debugging, in-system programming, and boundary-scan testing. Installed with ModusToolbox™ tools package, newer version may be available on GitHub. | [readme](https://github.com/Infineon/openocd/blob/cypress/README.MD) |
| ["Secure Boot" SDK](https://github.com/Infineon/cysecuretools) | This SDK includes all required libraries, tools, and sample code to provision and develop applications for PSoC™ 64 "Secure Boot" MCUs. | [User guide](https://www.cypress.com/documentation/software-and-drivers/psoc-64-secure-mcu-secure-boot-sdk-user-guide) |


## Board support packages

For any ModusToolbox™ application, you must specify a Board Support Package (BSP), which defines basic device features and capabilities. The BSP is a central feature of ModusToolbox™ software. The BSP specifies several critical items for the application, including:

- hardware configuration files for the device (for example, *design.modus*)
- startup code and linker files for the device
- other libraries that are required to support a kit

BSPs are aligned with our kits; they provide files for basic device functionality. A BSP typically has a *design.modus* file that configures clocks and other board-specific capabilities. That file is used by the ModusToolbox™ configurators. A BSP also includes the required device support code for the device on the board. You can modify the configuration to suit your application. 

We release BSPs independently of ModusToolbox™ software as a whole. This [search link](https://github.com/Infineon?q=TARGET_) finds all currently available BSPs on the GitHub site.

The search results include links to each repository, named TARGET_*kitnumber*. For example, you will find links to repositories like [TARGET_CY8CPROTO-062-4343W](https://github.com/Infineon/TARGET_CY8CPROTO-062-4343W). Each repository provides links to relevant documentation. The following links use this BSP as an example. Each BSP has its own documentation.

The information provided varies, but typically includes one or more of:

- an [API reference for the BSP](https://infineon.github.io/TARGET_CY8CPROTO-062-4343W/html/modules.html)
- the [BSP overview](https://infineon.github.io/TARGET_CY8CPROTO-062-4343W/html/md_bsp_boards_mt_bsp_user_guide.html)
- a link to the [associated kit page](https://www.cypress.com/documentation/development-kitsboards/psoc-6-wi-fi-bt-prototyping-kit-cy8cproto-062-4343w) with kit-specific documentation

A BSP is specific to a board and the device on that board. For custom development, you can create or modify a BSP for your device. See the [ModusToolbox™ user guide](http://www.cypress.com/ModusToolboxUserGuide) chapter on BSPs for how they work and how to create your own for a custom board.



## Libraries

There are many other parts of ModusToolbox™ software that are provided as libraries. When you create a ModusToolbox™ application, the system downloads all the libraries your application needs to take full advantage of the various features of our devices. A ModusToolbox™ application can use different libraries based on the Active BSP. 

#### Common libraries

##### Core libraries

Most BSPs typically add the following libraries as appropriate for the kit/device.

| Library                                            | Details                                                      | Docs                                                         |
| -------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [core-lib](https://github.com/Infineon/core-lib)   | Header files that declare basic types and utilities (such as result types or ASSERT) that can be used by multiple BSPs. | [API reference](https://infineon.github.io/core-lib/html/index.html) |
| [core-make](https://github.com/Infineon/core-make) | Core Make build system provides generic build files and scripts for building and programming ModusToolbox™ applications. | Repository [readme file](https://github.com/Infineon/core-make/blob/master/README.md) |

##### Abstraction Libraries 

| Library                                                      | Details                                                      | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [abstraction-rtos](https://github.com/Infineon/abstraction-rtos) | Abstraction layers provide APIs that allow different libraries to interact with each other without having to know specific details about a given library. This library provides a common API that allows code or middleware to use RTOS features. In the ModusToolbox™ Library Manager, this library is listed under "Abstraction Layer." | [API reference](https://infineon.github.io/abstraction-rtos/html/index.html) |

##### Board utilities

Different boards contain different peripherals or utilities (utils for short). The BSP automatically includes the utils libraries for that kit. For example, if the board contains an RGB LED, it will use the rgb-led library. The following show a few of the common utils that may be available for different boards. Your application may include different utils depending on your board's resources.

| Library                                                  | Details                                                      | Docs                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [retarget-io](https://github.com/Infineon/retarget-io)   | Provides a board-independent API to retarget text input/output to a serial UART on a kit | [API reference](https://infineon.github.io/retarget-io/html/index.html) |
| [serial-flash](https://github.com/Infineon/serial-flash) | Provides a board-independent API to use the serial flash on a kit | [API reference](https://infineon.github.io/serial-flash/html/index.html) |



#### Base libraries

##### PSoC™ 6 base libraries

A PSoC™ 6 BSP adds the following libraries as appropriate for the kit/device.

| Library                                                      | Details                                                      | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [mtb-hal-cat1](https://github.com/Infineon/mtb-hal-cat1)     | For the new MTB Flow, the PSoC™ 6 Hardware Abstraction Layer package provides a set of APIs to initialize, configure, and use the PSoC™ 6 MCU resources using our defined Hardware Abstraction Layer. | [API reference](https://infineon.github.io/mtb-hal-cat1/html/index.html) |
| [mtb-pdl-cat1](https://github.com/Infineon/mtb-pdl-cat1)     | For the new MTB Flow, the Peripheral Driver Library (PDL) integrates device header files, startup code, and low-level peripheral drivers into a single package. | [API reference](https://infineon.github.io/mtb-pdl-cat1/pdl_api_reference_manual/html/index.html) |
| [psoc6cm0p](https://github.com/Infineon/psoc6cm0p)           | Prebuilt application images for the Cortex M0+ CPU of a dual-CPU PSoC™ 6 MCU. | Repository [readme file](https://github.com/Infineon/psoc6cm0p/blob/master/README.md) |
| [psoc6make](https://github.com/Infineon/psoc6make)           | The build recipe Makefiles and scripts for building and programming PSoC™ 6 applications. You can build an application either through a command-line interface (CLI), the Eclipse IDE, or a third-party IDE. | Repository [readme file](https://github.com/Infineon/psoc6make/blob/master/README.md) |
| [recipe-make-cat1a](https://github.com/Infineon/recipe-make-cat1a) | For the new MTB Flow, the PSoC™ 6 Make build recipe provides the make files and scripts for building and programming PSoC™ 6 applications. | Repository [readme file](https://github.com/Infineon/recipe-make-cat1a/blob/master/README.md) |
| [psoc6hal](https://github.com/Infineon/psoc6hal)             | For the old LIB flow, the Hardware Abstraction Layer (HAL) provides a high-level interface to configure and use hardware blocks on our MCUs. It is a generic interface that can be used across multiple product families. The focus on ease-of-use and portability means the HAL does not expose all of the low-level peripheral functionality | [API reference](https://infineon.github.io/psoc6hal/html/index.html) |
| [psoc6pdl](https://github.com/Infineon/psoc6pdl)             | For the old LIB flow, the peripheral driver library for PSoC™ 6 MCUs. The library is device-independent, so it can be precompiled and used for any PSoC™ 6 MCU device or project. Included automatically by any BSP targeting a PSoC™ 6 MCU. | [API reference](https://infineon.github.io/psoc6pdl/pdl_api_reference_manual/html/index.html) |

##### PSoC™ 4 / PMG base libraries

PSoC™ 4 and PMG BSPs add the following libraries as appropriate for the kit/device.

| Library                                                      | Details                                                      | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [mtb-hal-cat2](https://github.com/Infineon/mtb-hal-cat2)     | PSoC™ 4 Hardware Abstraction Layer package, provides a set of APIs to initialize, configure, and use the PSoC™ 4 MCU resources using the Cypress defined Hardware Abstraction Layer. | [API reference](https://infineon.github.io/mtb-hal-cat2/html/index.html) |
| [mtb-pdl-cat2](https://github.com/Infineon/mtb-pdl-cat2)     | The Peripheral Driver Library (PDL) integrates device header files, startup code, and low-level peripheral drivers into a single package. | [API reference](https://infineon.github.io/mtb-pdl-cat2/pdl_api_reference_manual/html/index.html) |
| [recipe-make-cat2](https://github.com/Infineon/recipe-make-cat2) | PSoC™ 4 Make build recipe provides the make files and scripts for building and programming PSoC™ 4 applications. | Repository [readme file](https://github.com/Infineon/recipe-make-cat2/blob/master/README.md) |

##### XMC base libraries

An XMC MCU typically adds the following libraries, as appropriate for the kit/device.

| Library                                                      | Details                                                      | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [mtb-xmclib-cat3](https://github.com/Infineon/mtb-xmclib-cat3) | The XMC peripheral library (XMC Lib) consists of low-level drivers and CMSIS startup code for the XMC product family peripherals. | [API reference](https://infineon.github.io/mtb-xmclib-cat3/api_reference_manual/html/index.html) |
| [recipe-make-cat3](https://github.com/Infineon/recipe-make-cat3) | XMC Make build recipe provides the make files and scripts for building and programming XMC applications. | [API reference](https://infineon.github.io/recipe-make-cat3/api_reference_manual/html/index.html) |



#### MCU middleware libraries

For the various MCU BSPs, the following middleware libraries are typically available.

| Library                                                  | Details                                                      | Docs                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [clib-support](https://github.com/Infineon/clib-support) | The CLib FreeRTOS support library provides the necessary hooks to make C library functions such as malloc and free thread safe. | [API reference](https://infineon.github.io/clib-support/html/index.html) |
| [dfu](https://github.com/Infineon/dfu)                   | The Device Firmware Update (DFU) library provides an API for updating firmware images. | [API reference](https://infineon.github.io/dfu/dfu_sdk_api_reference_manual/html/index.html) |
| [emeeprom](https://github.com/Infineon/emeeprom)         | The Emulated EEPROM library provides an API to manage an emulated EEPROM in flash. It has support for wear leveling and restoring corrupted data from a redundant copy. | [API reference](https://infineon.github.io/emeeprom/em_eeprom_api_reference_manual/html/index.html) |
| [freertos](https://github.com/Infineon/freertos)         | FreeRTOS kernel, distributed as standard C source files with configuration header file, for use with the PSoC 6 MCU. | [FreeRTOS webpage](http://www.freertos.org/a00106.html)     |



#### PSoC™ 6 middleware libraries

For PSoC™ 6 MCUs, there are additional features on the device, including:

| Library                                          | Details                                                      | Docs                                                         |
| ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [bless](https://github.com/Infineon/bless)       | This library is specific to devices like **CY8C6347BZI-BLD53**, with onboard Bluetooth® and no separate connectivity device. The Bluetooth® Low Energy Subsystem (BLESS) library contains a comprehensive API to configure the Bluetooth® LE Stack and the underlying chip hardware. | [API reference](https://infineon.github.io/bless/ble_api_reference_manual/html/index.html) |
| [CAPSENSE™](https://github.com/Infineon/capsense) | Capacitive sensing can be used in a variety of applications and products where conventional mechanical buttons can be replaced with sleek human interfaces to transform the way users interact with electronic systems. | [API reference](https://infineon.github.io/capsense/capsense_api_reference_manual/html/index.html) |
| [csdadc](https://github.com/Infineon/csdadc)     | Enables the ADC functionality of the CAPSENSE™ Sigma-Delta (CSD) hardware block. Useful for devices that do not include other ADC/IDAC options. | [API reference](https://infineon.github.io/csdadc/csdadc_api_reference_manual/html/index.html) |
| [csdidac](https://github.com/Infineon/csdidac)   | The same, for IDAC functionality.                            | [API reference](https://infineon.github.io/csdidac/csdidac_api_reference_manual/html/index.html) |
| [emeeprom](https://github.com/Infineon/emeeprom) | The Emulated EEPROM library provides an API to manage an emulated EEPROM in flash. It has support for wear leveling and restoring corrupted data from a redundant copy. | [API reference](https://infineon.github.io/emeeprom/em_eeprom_api_reference_manual/html/index.html) |
| [emwin](https://github.com/Infineon/emwin)       | SEGGER embedded graphic library and graphical user interface (GUI) framework designed to provide processor- and display controller-independent GUI for any application that needs a graphical display. | [Overview](https://infineon.github.io/middleware-emwin/emwin_overview/html/index.html) |
| [usbdev](https://github.com/Infineon/usbdev)     | The USB Device library provides a full-speed USB 2.0 Chapter 9 specification compliant device framework. | [API reference](https://infineon.github.io/usbdev/usbfs_dev_api_reference_manual/html/index.html) |



#### Bluetooth® BSP libraries

***BTSDK v2.8 and later Structure***
In the ModusToolbox™ environment for BTSDK v2.8, BSPs and libraries use the new MTB flow. In this flow, there are the following libraries.

##### BTSDK core support

| Library                                                      | Details                                      |
| ------------------------------------------------------------ | -------------------------------------------- |
| [BTSDK shared source](https://github.com/Infineon/btsdk-common) | BTSDK shared source used by applications.    |
| [BTSDK shared includes](https://github.com/Infineon/btsdk-include) | BTSDK shared headers used for all platforms. |
| [BTSDK tools](https://github.com/Infineon/btsdk-tools)       | BTSDK shared tools used for all platforms.   |

##### BTSDK CSP base libraries

| Library                                           | Details                                                      | Docs                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [CYW20706A2](https://github.com/Infineon/20706A2) | BTSDK CSP base library providing core support for CYW20706A2 devices. | [API reference](https://infineon.github.io/btsdk-docs/BT-SDK/20706-A2_Bluetooth/API/index.html) |
| [CYW20719B2](https://github.com/Infineon/20719B2) | BTSDK CSP base library providing core support for CYW20719B2 devices. | [API reference](https://infineon.github.io/btsdk-docs/BT-SDK/20719-B2_Bluetooth/API/index.html) |
| [CYW20721B2](https://github.com/Infineon/20721B2) | BTSDK CSP base library providing core support for CYW20721B2 devices. | [API reference](https://infineon.github.io/btsdk-docs/BT-SDK/20721-B2_Bluetooth/API/index.html) |
| [CYW20735B1](https://github.com/Infineon/20735B1) | BTSDK CSP base library providing core support for CYW20735B1 devices. | [API reference](https://infineon.github.io/btsdk-docs/BT-SDK/20735-B1_Bluetooth/API/index.html) |
| [CYW20819A1](https://github.com/Infineon/20819A1) | BTSDK CSP base library providing core support for CYW20819A1 devices. |                                                              |
| [CYW20820A1](https://github.com/Infineon/20820A1) | BTSDK CSP base library providing core support for CYW20820A1 devices. |                                                              |
| [CYW20835B1](https://github.com/Infineon/20835B1) | BTSDK CSP base library providing core support for CYW20835B1 devices. | [API reference](https://infineon.github.io/btsdk-docs/BT-SDK/20835-B1_Bluetooth/API/index.html) |
| [CYW43012C0](https://github.com/Infineon/43012C0) | BTSDK CSP base library providing core support for CYW43012C0 devices. | [API reference](https://infineon.github.io/btsdk-docs/BT-SDK/43012-C0_Bluetooth/API/index.html) |

##### BTSDK shared source libraries

- [btsdk-audio](https://github.com/Infineon/btsdk-audio) 
- [btsdk-ble](https://github.com/Infineon/btsdk-ble) 
- [btsdk_drivers](https://github.com/Infineon/btsdk-drivers) 
- [btsdk-hid](https://github.com/Infineon/btsdk-hid) 
- [btsdk-include](https://github.com/Infineon/btsdk-include) 
- [btsdk-mesh](https://github.com/Infineon/btsdk-mesh) 
- [btsdk-ota](https://github.com/Infineon/btsdk-ota) 
- [btsdk-rfcomm](https://github.com/Infineon/btsdk-rfcomm) 
- [btsdk-utils](https://github.com/Infineon/btsdk-utils) 
- [btsdk-host-apps-bt-ble](https://github.com/Infineon/btsdk-host-apps-bt-ble) 
- [btsdk-host-apps-mesh](https://github.com/Infineon/btsdk-host-apps-mesh) 
- [btsdk-peer-apps-bel](https://github.com/Infineon/btsdk-peer-apps-ble) 
- [btsdk-peer-apps-mesh](https://github.com/Infineon/btsdk-peer-apps-mesh) 
- [btsdk-peer-apps-ota](https://github.com/Infineon/btsdk-peer-apps-ota) 


##### BTSDK utilities and host/peer apps

| Library                                                      | Details                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [BTSDK host apps](https://github.com/Infineon/btsdk-host-apps-bt-ble) | Windows, Linux, and macOS based host apps for Bluetooth® and Bluetooth® LE such as ClientControl. |
| [BTSDK Host and peer apps for mesh](https://github.com/Infineon/btsdk-host-peer-apps-mesh) | Windows, Linux, and macOS based host apps to control Bluetooth® LE Mesh embedded apps, as well as Windows, Android, and iOS based peer apps to configure and provision Bluetooth® LE Mesh embedded apps. |
| [BTSDK peer apps for Bluetooth® LE](https://github.com/Infineon/btsdk-peer-apps-ble) | Windows, Android, and iOS based peer apps for Bluetooth® LE such as hello_sensor. |
| [BTSDK peer apps for OTA](https://github.com/Infineon/btsdk-peer-apps-ota) | Windows, Linux, and macOS based peer apps for OTA app.       |
| [BTSDK utilities](https://github.com/Infineon/btsdk-utils)   | BTSDK shared utilities usable for all platforms, including BTSpy. |

***BTSDK v2.7 and earlier Structure***
In the ModusToolbox™ environment for BTSDK v2.7, BSPs and libraries use the LIB flow. You must create the "wiced_btsdk" code example first. That creates a local instance of the entire SDK on your computer. Follow the instructions in the the Project Creator tool. For more details about the WICED BTSDK, refer to https://infineon.github.io/btsdk-docs/BT-SDK/index.html.



#### AnyCloud libraries

AnyCloud is based on the industry standard lwIP TCP/IP stack and Mbed TLS network security. These libraries provide core functionality including connectivity, security, firmware upgrade support, and application layer protocols for applications that do not use commercial cloud management systems.

| Library                                                      | Description                                                  | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wifi-mw-core](https://github.com/Infineon/wifi-mw-core)     | The Wi-Fi Middleware Core library bundles the core libraries that any Wi-Fi application needs. | [API reference](https://infineon.github.io/wifi-mw-core/api_reference_manual/html/index.html) |
| [wifi-connection-manager](https://github.com/Infineon/wifi-connection-manager) | The Wi-Fi Connection Manager (WCM) includes the wifi-mw-core library by default and provides easy to use APIs to establish and monitor Wi-Fi connections on our devices that support Wi-Fi connectivity. | [API reference](https://infineon.github.io/wifi-connection-manager/api_reference_manual/html/index.html) |
| [wifi-host-driver](https://github.com/Infineon/wifi-host-driver) | The Wi-Fi Host Driver (WHD) is an independent, embedded driver that provides a set of APIs to interact with Cypress WLAN chips. | [API reference](https://infineon.github.io/wifi-host-driver/API/index.html) |
| [anycloud-ota](https://github.com/Infineon/anycloud-ota)     | This Over-The-Air (OTA) library enables applications to implement sophisticated OTA software updates from any cloud platform using custom cloud management tools. | [API reference](https://infineon.github.io/anycloud-ota/api_reference_manual/html/index.html) |
| [mqtt](https://github.com/Infineon/mqtt)                     | This library includes the open source AWS IoT device SDK embedded C library plus some glue to ensure seamless MQTT cloud connectivity. | [API reference](https://infineon.github.io/mqtt/api_reference_manual/html/index.html) |
| [secure-sockets](https://github.com/Infineon/secure-sockets) | The Secure Sockets library eases application development by exposing a socket like interface for both secured and non-secured socket communication. | [API reference](https://infineon.github.io/secure-sockets/api_reference_manual/html/index.html) |
| lwIP                                                         | This is a lightweight open-source TCP/IP stack.              | [External website](http://www.nongnu.org/lwip/2_1_x/index.html) |
| [cy-mbedtls-acceleration](https://github.com/Infineon/cy-mbedtls-acceleration) | We provide a library that extends MbedTLS to enable hardware-accelerated encryption on PSoC™ 6 MCUs. | [Arm Mbed TLS](https://github.com/ARMmbed/mbedtls)           |
| [lpa](https://github.com/Infineon/lpa)                       | The Low Power Assistant (LPA) is a library and associated settings in the ModusToolbox™ Device Configurator that allow you to configure a PSoC 6 Host and WLAN (Wi-Fi / BT Radio) device for optimized low-power operation. | [API reference](https://infineon.github.io/lpa/lpa_api_reference_manual/html/index.html) |
| [bluetooth-freertos](https://github.com/Infineon/bluetooth-freertos) | AIROC™ Bluetooth® host stack solution includes Bluetooth® stack library, Bluetooth® controller firmware, and platform/OS porting layer. | [API reference](https://infineon.github.io/bluetooth-freertos/api_reference_manual/html/index.html) |
| [btstack](https://github.com/Infineon/btstack)               | BTSTACK is our Bluetooth® Host Protocol Stack implementation. The stack is optimized to work on our Bluetooth® controllers. | [API reference](https://infineon.github.io/btstack/ble/api_reference_manual/html/index.html) [Dual Mode API reference](https://infineon.github.io/btstack/dual_mode/api_reference_manual/html/index.html) |
| [connectivity-utilities](https://github.com/Infineon/connectivity-utilities) | General purpose middleware connectivity utilities, for instance a linked_list or a json_parser. This library is supported on both AnyCloud and Mbed OS. | See the code for each.                                       |



#### Libraries for third-party systems

ModusToolbox™ software supports some third-party IoT ecosystems, like AWS IoT. Vendors typically provide libraries for their ecosystem. We extend some vendors' libraries to provide support for our devices (like aws-iot), provides a utility to make working with an ecosystem library easier (like http-server), and uses some open source libraries as they are (like Arm MBed TLS).

| Library                                                      | Details                                                      | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [aws-iot](https://github.com/Infineon/aws-iot)               | Provides secured, bi-directional communication between Internet-connected devices such as sensors, actuators, embedded micro-controllers, or smart appliances and the AWS Cloud. Supports MQTT and HTTP protocols. | [Developer guide](https://docs.aws.amazon.com/iot/latest/developerguide/what-is-aws-iot.html) |
| [enterprise-security](https://github.com/Infineon/enterprise-security) | This library implements a collection of the most commonly used Extensible Authentication Protocols (EAP) used in enterprise Wi-Fi networks | [API reference](https://infineon.github.io/enterprise-security/api_reference_manual/html/index.html) |
| [http-server](https://github.com/Infineon/http-server)       | Provides communication functions for an HTTP server.         | [readme](https://github.com/Infineon/http-server/blob/master/README.md) |
| [connectivity-utilities](https://github.com/Infineon/connectivity-utilities) | General purpose middleware connectivity utilities, for instance a linked_list or a json_parser. This library is supported on both AnyCloud and Mbed OS. | See the code for each.                                       |
| Mbed OS HAL                                                  | Mbed’s hardware abstraction layer. Support for Cypress targets is available from the Mbed OS archive. This HAL is part of the Mbed ecosystem and not provided directly by Cypress. | [Mbed API documentation](https://os.mbed.com/docs/mbed-os/v5.13/apis/index.html) |
| Arm Mbed TLS                                                 | A library to include cryptographic and SSL/TLS capabilities in an embedded application. It is part of the Mbed OS ecosystem and not provided by Cypress. | [API reference](https://tls.mbed.org/api/)                   |
