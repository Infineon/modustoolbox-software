# ModusToolbox™ software

ModusToolbox™ software is a modern, extensible development environment supporting a wide range of Infineon microcontroller devices. It provides a flexible set of tools and a diverse, high-quality collection of application-focused software. These include configuration tools, low-level drivers, libraries, and operating system support, most of which are compatible with Linux, macOS, and Windows-hosted environments. 

This page helps you identify and find the ModusToolbox™ resources available. These resources are grouped in the following top-level categories:

- [Tools](#tools)
- [Code examples](https://github.com/Infineon/Code-Examples-for-ModusToolbox-Software) (link to separate page)
- [Board support packages](#board-support-packages)
- [Libraries](#libraries)
- [Training material](https://github.com/Infineon/training-modustoolbox) (link to separate page)

## Tools

The ModusToolbox™ tools package installer (https://www.infineon.com/cms/en/design-support/tools/sdk/modustoolbox-software) provides various multi-platform development tools to help you work in your preferred flow. The installer includes a make-based build system, Eclipse IDE, configurators, stand-alone project creator and library manager, as well as support for using other IDEs, generating code, compiling, programming, and debugging. Refer to the [ModusToolbox™ tools package user guide](https://www.Infineon.com/ModusToolboxUserGuide) for complete details.

Some tools are available separately on GitHub, including:

| Tool | Description | Docs |
| ---- | ----------- | ---- |
| [Firmware-loader](https://github.com/Infineon/Firmware-loader) | A command-line tool to update KitProg low-level program/debug communication firmware on our kits. Installed with ModusToolbox™ tools package, newer version may be available on GitHub. | [readme](https://github.com/Infineon/Firmware-loader/blob/master/README.md) |
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

A BSP is specific to a board and the device on that board. For custom development, you can create or modify a BSP for your device. See the [ModusToolbox™ tools package user guide](http://www.Infineon.com/ModusToolboxUserGuide) chapter on BSPs for how they work and how to create your own for a custom board.


## Libraries

There are many other parts of ModusToolbox™ software that are provided as libraries. In general, you should not need to use these libraries directly. When you create a ModusToolbox™ application, the system downloads all the libraries your application needs to take full advantage of the various features of our devices. A ModusToolbox™ application can use different libraries based on the Active BSP. If you wish to add various libraries to your application, use the Library Manager tool.  

The following tables provide brief descriptions about the libraries available and links to the various repos. Refer to the [ModusToolbox™ run-time software reference guide](https://www.infineon.com/ModusToolboxRuntimeSoftwareReferenceGuide) for more details about how these libraries are used in the ModusToolbox™ ecosystem.

<details><summary><b>Drivers and Core Middleware</b></summary>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [core-lib](https://github.com/Infineon/core-lib)   | Header files that declare basic types and utilities (such as result types or ASSERT) that can be used by multiple BSPs. | [API reference](https://infineon.github.io/core-lib/html/index.html) |
| [cmsis](https://github.com/ARM-software/CMSIS_5) | used by application or middleware to link CMSIS Core headers | [README](https://github.com/ARM-software/CMSIS_5#readme) |
| [freertos](https://github.com/Infineon/freertos)         | FreeRTOS kernel, distributed as standard C source files with configuration header file, for use with the PSoC 6 MCU. | [FreeRTOS webpage](http://www.freertos.org/a00106.html)     |
| [freertos-posix](https://github.com/Infineon/freertos-posix) | The Portable Operating System Interface (POSIX) is a family of standards specified by the IEEE Computer Society for maintaining compatibility between operating systems. freertos-posix implements a small subset of the POSIX threading API. | [POSIX API Reference](http://pubs.opengroup.org/onlinepubs/9699919799/) |
| [command console](https://github.com/Infineon/command-console) | Provides a framework to add command console support to the application (or) product use cases.  | [API reference](https://infineon.github.io/command-console/api_reference_manual/html/index.html)
| [csdadc](https://github.com/Infineon/csdadc)     | Enables the ADC functionality of the CAPSENSE™ Sigma-Delta (CSD) hardware block. Useful for devices that do not include other ADC/IDAC options. | [API reference](https://infineon.github.io/csdadc/csdadc_api_reference_manual/html/index.html) |
| [csdidac](https://github.com/Infineon/csdidac)   | The same, for IDAC functionality.                            | [API reference](https://infineon.github.io/csdidac/csdidac_api_reference_manual/html/index.html) |
| [emeeprom](https://github.com/Infineon/emeeprom) | The Emulated EEPROM library provides an API to manage an emulated EEPROM in flash. It has support for wear leveling and restoring corrupted data from a redundant copy. | [API reference](https://infineon.github.io/emeeprom/em_eeprom_api_reference_manual/html/index.html) |
| [emfile](https://github.com/Infineon/emfile)  | A FAT16/32 filesystem for embedded systems supporting SPI NOR flash and SD card. | [User guide](https://github.com/Infineon/emfile/blob/master/Doc/User_Guide.md) | 
| [emusb-host](https://github.com/infineon/emusb-host) | CPU-independent USB Host stack. | [API reference](https://infineon.github.io/emusb-host/html/index.html) |
| [emusb-device](https://github.com/infineon/emusb-device) | Enables easy integration of USB functionality into an embedded system. | [API reference](https://infineon.github.io/emusb-device/html/index.html) |
| [usbdev](https://github.com/Infineon/usbdev)     | The USB Device library provides a full-speed USB 2.0 Chapter 9 specification compliant device framework. | [API reference](https://infineon.github.io/usbdev/usbfs_dev_api_reference_manual/html/index.html) |
| [littlefs](https://github.com/littlefs-project/littlefs)  | A little fail-safe filesystem designed for microcontrollers.  | [README](https://github.com/littlefs-project/littlefs#readme)  |
| [mtb-littlefs](https://github.com/Infineon/mtb-littlefs) | Provides a set of block device drivers for use with the littlefs file system.  | [API reference](https://infineon.github.io/mtb-littlefs/api_reference_manual/html/index.html)  |
| [abstraction-rtos](https://github.com/Infineon/abstraction-rtos) | Abstraction layers provide APIs that allow different libraries to interact with each other without having to know specific details about a given library. This library provides a common API that allows code or middleware to use RTOS features. In the ModusToolbox™ Library Manager, this library is listed under "Abstraction Layer." | [API reference](https://infineon.github.io/abstraction-rtos/html/index.html) |
| [clib-support](https://github.com/Infineon/clib-support) | The CLib FreeRTOS support library provides the necessary hooks to make C library functions such as malloc and free thread safe. | [API reference](https://infineon.github.io/clib-support/html/index.html) |
| [retarget-io](https://github.com/Infineon/retarget-io)   | Provides a board-independent API to retarget text input/output to a serial UART on a kit | [API reference](https://infineon.github.io/retarget-io/html/index.html) |
| [serial-flash](https://github.com/Infineon/serial-flash) | Provides a board-independent API to use the serial flash on a kit | [API reference](https://infineon.github.io/serial-flash/html/index.html) |

<b>CAT1: PSoC™ 6, CYW20829, TRAVEO™ II, XMC7000</b>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [cat1cm0p](https://github.com/Infineon/cat1cm0p) | Arm® Cortex®-M0+ prebuilt images enabling flash write services and Bluetooth® Low Energy event handling. | [README](https://github.com/Infineon/cat1cm0p#readme) |
| [mtb-hal-cat1](https://github.com/Infineon/mtb-hal-cat1)  | The PSoC™ 6 Hardware Abstraction Layer package provides a set of APIs to initialize, configure, and use the PSoC™ 6 MCU resources using our defined Hardware Abstraction Layer. | [API reference](https://infineon.github.io/mtb-hal-cat1/html/index.html) |
| [mtb-pdl-cat1](https://github.com/Infineon/mtb-pdl-cat1)  | The Peripheral Driver Library (PDL) integrates device header files, startup code, and low-level peripheral drivers into a single package. | [API reference](https://infineon.github.io/mtb-pdl-cat1/pdl_api_reference_manual/html/index.html) |

<b>CAT2: PSoC™ 4, PMG</b>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [mtb-hal-cat2](https://github.com/Infineon/mtb-hal-cat2)     | PSoC™ 4 Hardware Abstraction Layer package, provides a set of APIs to initialize, configure, and use the PSoC™ 4 MCU resources using the defined Hardware Abstraction Layer. | [API reference](https://infineon.github.io/mtb-hal-cat2/html/index.html) |
| [mtb-pdl-cat2](https://github.com/Infineon/mtb-pdl-cat2)     | The Peripheral Driver Library (PDL) integrates device header files, startup code, and low-level peripheral drivers into a single package. | [API reference](https://infineon.github.io/mtb-pdl-cat2/pdl_api_reference_manual/html/index.html) |

<b>CAT3: XMC1000, XMC4000</b>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [mtb-xmclib-cat3](https://github.com/Infineon/mtb-xmclib-cat3) | The XMC peripheral library (XMC Lib) consists of low-level drivers and CMSIS startup code for the XMC product family peripherals. | [API reference](https://infineon.github.io/mtb-xmclib-cat3/xmc1_api_reference_manual/html/index.html) |

<b>CAT4: CYW43907, CYW54907</b>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [mtb-hal-cat4](https://github.com/Infineon/mtb-hal-cat4) | Hardware Abstraction Layer package, provides a set of APIs to initialize, configure, and use the CYW43907/CYW54907 resources using the defined Hardware Abstraction Layer. | [API reference](https://infineon.github.io/mtb-hal-cat4/html/index.html) |

</details>

<details><summary><b>ModusToolbox™ for Connectivity</b></summary>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [aws-iot-device-sdk-embedded-C](https://github.com/aws/aws-iot-device-sdk-embedded-C)  | Collection of C source files under the MIT open source license that can be used in embedded applications to securely connect IoT devices to AWS IoT Core.  | [README.md](https://github.com/aws/aws-iot-device-sdk-embedded-C/blob/main/README.md)  |
| [aws-iot-device-sdk-port](https://github.com/Infineon/aws-iot-device-sdk-port)  | Contains the port layer implementation for the MQTT and HTTP Client libraries to work with the AWS-IoT-Device-SDK-Embedded-C library on PSoC™ 6 MCU based platforms with network connectivity.  | [API Reference](https://infineon.github.io/aws-iot-device-sdk-port/api_reference_manual/html/index.html) |
| [azure-c-sdk-port](https://github.com/Infineon/azure-c-sdk-port)  | Implements the port layer for the Azure SDK for Embedded C to work on PSoC™ 6 MCU based platforms with network connectivity.  | [API reference](https://infineon.github.io/azure-c-sdk-port/api_reference_manual/html/index.html)  |
| [azure-sdk-for-c](https://github.com/Azure/azure-sdk-for-c) | Allows small embedded (IoT) devices to communicate with Azure services. | [README](https://github.com/Azure/azure-sdk-for-c#readme)  |
| [http-client](https://github.com/Infineon/http-client)  | Provides the HTTP Client implementation that can work on the PSoC™ 6 MCU platforms with Wi-Fi connectivity.   | [API reference](https://infineon.github.io/http-client/api_reference_manual/html/index.html)  |
| [http-server](https://github.com/Infineon/http-server)  | Provides communication functions for an HTTP server. | [README](https://github.com/Infineon/http-server/blob/master/README.md) |
| [lpa](https://github.com/Infineon/lpa) | The Low Power Assistant (LPA) is a library and associated settings in the ModusToolbox™ Device Configurator that allow you to configure a PSoC 6 Host and WLAN (Wi-Fi / BT Radio) device for optimized low-power operation. | [API reference](https://infineon.github.io/lpa/lpa_api_reference_manual/html/index.html) |
| [mqtt](https://github.com/Infineon/mqtt)  | This library includes the open source AWS IoT device SDK embedded C library plus some glue to ensure seamless MQTT cloud connectivity. | [API reference](https://infineon.github.io/mqtt/api_reference_manual/html/index.html) |
| [secure-sockets](https://github.com/Infineon/secure-sockets) | The Secure Sockets library eases application development by exposing a socket like interface for both secured and non-secured socket communication. | [API reference](https://infineon.github.io/secure-sockets/api_reference_manual/html/index.html) |
| [connectivity-utilities](https://github.com/Infineon/connectivity-utilities) | General purpose middleware connectivity utilities, for instance a linked_list or a json_parser. | [API reference](https://infineon.github.io/connectivity-utilities/api_reference_manual/html/index.html) |
| [ota-update](https://github.com/infineon/ota-update/)| TProvides support for Over-The-Air update of the application code running on a PSoC™ 6 MCU with AIROC™ CYW4343W or CYW43012 Wi-Fi & Bluetooth® combo chip, using Wi-Fi or Bluetooth®. | [API reference](https://infineon.github.io/ota-update/api_reference_manual/html/index.html) |
| [netxduo](https://github.com/azure-rtos/netxduo) | Advanced, industrial-grade TCP/IP network stack designed specifically for deeply embedded real-time and IoT applications. | [README](https://github.com/azure-rtos/netxduo#readme) |
| [memfault-firmware-sdk](https://github.com/memfault/memfault-firmware-sdk) | An SDK responsible for working with Memfault device monitoring, debugging and OTA management platform. | [External README](https://github.com/memfault/memfault-firmware-sdk/blob/master/README.md) |
| [golioth-firmware-sdk](https://github.com/golioth/golioth-firmware-sdk) | A software development kit for connecting embedded devices to the Golioth IoT Cloud | [External README](https://github.com/golioth/golioth-firmware-sdk/blob/main/README.md) |
| [lwIP](http://www.nongnu.org/lwip/2_1_x/index.html) | Lightweight open-source TCP/IP stack. | [External website](http://www.nongnu.org/lwip/2_1_x/index.html) |
| [virtual-connectivity-manager](https://github.com/Infineon/virtual-connectivity-manager) | Virtual-Connectivity-Manager (VCM) is a library that enables connectivity libraries to add multi-core support through virtualization. Virtualization allows the connectivity stack running on one core to be accessed from another core using Inter Process Communication (IPC). | [API reference](https://infineon.github.io/virtual-connectivity-manager/api_reference_manual/html/index.html) |

</details>

<details><summary><b>ModusToolbox™ for Wi-Fi</b></summary>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [wifi-mw-core](https://github.com/Infineon/wifi-mw-core)     | The Wi-Fi Middleware Core library bundles the core libraries that any Wi-Fi application needs. | [API reference](https://infineon.github.io/wifi-mw-core/api_reference_manual/html/index.html) |
| [wifi-host-driver](https://github.com/Infineon/wifi-host-driver) | The Wi-Fi Host Driver (WHD) is an independent, embedded driver that provides a set of APIs to interact with our WLAN chips. | [API reference](https://infineon.github.io/wifi-host-driver/API/index.html) |
| [wifi-connection-manager](https://github.com/Infineon/wifi-connection-manager) | The Wi-Fi Connection Manager (WCM) includes the wifi-mw-core library by default and provides easy to use APIs to establish and monitor Wi-Fi connections on our devices that support Wi-Fi connectivity. | [API reference](https://infineon.github.io/wifi-connection-manager/api_reference_manual/html/index.html) |
| [smartcoex](https://github.com/Infineon/smartcoex) |Provides an API to configure the coex parameters for WLAN and Bluetooth® Low Energy on PSoC™ 6 MCU based platforms with Wi-Fi & Bluetooth® combo chip. | [API reference](https://infineon.github.io/smartcoex/api_reference_manual/html/index.html)  |
| [enterprise-security](https://github.com/Infineon/enterprise-security) | This library implements a collection of the most commonly used Extensible Authentication Protocols (EAP) used in enterprise Wi-Fi networks | [API reference](https://infineon.github.io/enterprise-security/api_reference_manual/html/index.html) |
| [wpa3-external-supplicant](https://github.com/Infineon/wpa3-external-supplicant) | The WPA3 External Supplicant supports WPA3 SAE authentication using HnP (Hunting and Pecking Method) using RFC, as well as H2E (Hash to Element Method) using RFC following 802.11 spec 2016. | [README](https://github.com/Infineon/wpa3-external-supplicant/blob/master/README.md) |

</details>

<details><summary><b>ModusToolbox™ for Bluetooth®</b></summary>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [ble-mesh](https://github.com/Infineon/ble-mesh) | Provides Application Programming Interfaces (APIs) for application developers to use and create Mesh Applications. | [API reference](https://infineon.github.io/ble-mesh/api_reference_manual/html/index.html) |
| [btstack](https://github.com/Infineon/btstack) | BTSTACK is our Bluetooth® Host Protocol Stack implementation. The stack is optimized to work on our Bluetooth® controllers. | [API reference](https://infineon.github.io/btstack/ble/api_reference_manual/html/index.html) [Dual Mode API reference](https://infineon.github.io/btstack/dual_mode/api_reference_manual/html/index.html) |
| [btstack-integration](https://github.com/Infineon/btstack-integration) | Platform adaptation layer (porting layer) between AIROC™ BT Stack and Abstraction Layers (CYHAL and CYOSAL) for different hardware platforms.  | [README](https://github.com/Infineon/btstack-integration#readme)   |
| [bless](https://github.com/Infineon/bless)  | This library is specific to devices like **CY8C6347BZI-BLD53**, with onboard Bluetooth® and no separate connectivity device. The Bluetooth® Low Energy Subsystem (BLESS) library contains a comprehensive API to configure the Bluetooth® LE Stack and the underlying chip hardware. | [API reference](https://infineon.github.io/bless/ble_api_reference_manual/html/index.html) |

For information about <b>BTSDK</b>, see [https://Infineon.github.io/btsdk-docs/BT-SDK/index.html](https://Infineon.github.io/btsdk-docs/BT-SDK/index.html).

</details>

<details><summary><b>ModusToolbox™ for Graphics</b></summary>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [emwin](https://github.com/Infineon/emwin)       | SEGGER embedded graphic library and graphical user interface (GUI) framework designed to provide processor- and display controller-independent GUI for any application that needs a graphical display. | [Overview](https://infineon.github.io/middleware-emwin/emwin_overview/html/index.html) |

</details>

<details><summary><b>ModusToolbox™ for Security</b></summary>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [trusted-firmware-m](https://github.com/Infineon/trusted-firmware-m) | Provides secure world software for Arm Cortex-M processors.  | [README](https://github.com/Infineon/trusted-firmware-m#readme)  |
| [dfu](https://github.com/Infineon/dfu)  | The Device Firmware Update (DFU) library provides an API for updating firmware images. | [API reference](https://infineon.github.io/dfu/dfu_sdk_api_reference_manual/html/index.html) |
| [Arm Mbed TLS](https://github.com/ARMmbed/mbedtls) | A library to include cryptographic and SSL/TLS capabilities in an embedded application. | [API reference](https://tls.mbed.org/api/) |
| [cy-mbedtls-acceleration](https://github.com/Infineon/cy-mbedtls-acceleration) | We provide a library that extends MbedTLS to enable hardware-accelerated encryption on PSoC™ 6 MCUs. | [README](https://github.com/Infineon/cy-mbedtls-acceleration#readme) |
| [MCUBoot](https://github.com/mcu-tools/mcuboot) | Secure bootloader for 32-bits microcontrollers.  | [README](https://github.com/mcu-tools/mcuboot#readme) |

</details>

<details><summary><b>ModusToolbox™ for Machine Learning</b></summary>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [ml-inference](https://github.com/Infineon/ml-inference) | A set of pre-compiled libraries which provide easy to use API's to run ML workloads on embedded platforms.  | [API reference](https://infineon.github.io/ml-inference/html/index.html) |
| [ml-middleware](https://github.com/Infineon/ml-middleware) | Helper functions to simplify integration of ML models. | [API reference](https://infineon.github.io/ml-middleware/html/index.html) |
| [ml-tflite-micro](https://github.com/Infineon/ml-tflite-micro) | A pre-configured TensorFlow tflite-micro runtime library for the Infineon PSoC6™ platform. | [README](https://github.com/Infineon/ml-tflite-micro#readme) |

</details>

<details><summary><b>ModusToolbox™ for Voice</b></summary>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [cyberon-dspotter-lib-psoc6-cm0p](https://github.com/CyberonEBU/cyberon-dspotter-lib-psoc6-cm0p) | Highly-accurate and lightweight wake word engine. It enables building always-listening voice-enabled applications for the CM0p Infineon devices | [External website](https://www.renesas.com/us/en/products/microcontrollers-microprocessors/ra-cortex-m-mcus/ra-partners/cyberon-dspotter) |
| [cyberon-dspotter-lib-psoc6-cm4](https://github.com/CyberonEBU/cyberon-dspotter-lib-psoc6-cm4) | Highly-accurate and lightweight wake word engine. It enables building always-listening voice-enabled applications for the CM4 Infineon devices | [External website](https://www.renesas.com/us/en/products/microcontrollers-microprocessors/ra-cortex-m-mcus/ra-partners/cyberon-dspotter) |

</details>

</details>

<details><summary><b>ModusToolbox™ for HMI</b></summary>

| Library  | Details  | Docs  |
| -------- | -------- | ----- |
| [CAPSENSE™](https://github.com/Infineon/capsense) | Capacitive sensing can be used in a variety of applications and products where conventional mechanical buttons can be replaced with sleek human interfaces to transform the way users interact with electronic systems. | [API reference](https://infineon.github.io/capsense/capsense_api_reference_manual/html/index.html) |

</details>
