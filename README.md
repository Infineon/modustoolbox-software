# PSoC® 6 Enablement Software

As a developer, you have preferred tools and workflows for creating products. What you need is enablement software you can use seamlessly in your existing environment. This document lists and describes what's available to you. ModusToolbox software is:

- Comprehensive – it has the resources you need
- Flexible – you can use the resources in your own workflow
- Atomic – you can get just the resources you want

ModusToolbox software encompasses a variety of software resources, organized in this document into:

[Low-Level Resources](#low-level-resources)

[Board Support Packages](#board-support-packages)

[Middleware](#middleware)

See the [ModusToolbox Software Overview](https://www.cypress.com/ModusToolboxSWOverview) document to understand how all this works. Some libraries are intended for development in a particular ecosystem, like Mbed OS.

Each library is delivered in its own repository, complete with documentation. Both Cypress and third-party middleware is available. The information below includes links to each repository, and various resources associated with each library. Go to each repository to see what releases are available for that library. 

Cypress also provides a [comprehensive set of code examples](https://github.com/cypresssemiconductorco/Code-Examples-for-ModusToolbox-Software) covering most if not all functionality in the provided software. In ModusToolbox, a code example (also called a starter app) automatically incorporates all libraries required for the application. 

You do not need to clone or download anything. Each repository is available should you wish to get a local copy or a particular release for your development environment.

------

## Low-Level Resources

BSPs include the low-level resources required for a particular kit. If you build a starter application using either the ModusToolbox IDE or the stand-alone Project Creator tool, you do not need to download or clone these repositories separately. They are included automatically by the build infrastructure.

| Item                                                         | Details                                                      | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [psoc6hal](https://github.com/cypresssemiconductorco/psoc6hal) | The Hardware Abstraction Layer (HAL) provides a high-level interface to configure and use hardware blocks on Cypress MCUs. It is a generic interface that can be used across multiple product families. The focus on ease-of-use and portability means the HAL does not expose all of the low-level peripheral functionality | [API   Reference](https://cypresssemiconductorco.github.io/psoc6hal/html/index.html) |
| [abstraction-rtos](https://github.com/cypresssemiconductorco/abstraction-rtos) | A common API that allows code or middleware to use RTOS features without knowing what the RTOS is | [API   Reference](https://cypresssemiconductorco.github.io/abstraction-rtos/html/index.html) |
| [core-lib](https://github.com/cypresssemiconductorco/core-lib) | Provides header files that declare basic types and utilities (such as result types or ASSERT) that can be used by multiple BSPs | [API   Reference](https://cypresssemiconductorco.github.io/core-lib/html/index.html) |
| [retarget-io](https://github.com/cypresssemiconductorco/retarget-io) | Provides a board-independent API to retarget text input/ouput to a serial UART on a kit | [API   Reference](https://cypresssemiconductorco.github.io/retarget-io/html/index.html) |
| [rgb-led](https://github.com/cypresssemiconductorco/rgb-led) | Provides a board-independent API to use the RGB LED on a kit | [API   Reference](https://cypresssemiconductorco.github.io/rgb-led/html/index.html) |
| [serial-flash](https://github.com/cypresssemiconductorco/serial-flash) | Provides a board-independent API to use the serial flash on a kit | [API   Reference](https://cypresssemiconductorco.github.io/serial-flash/html/index.html) |
| [psoc6pdl](https://github.com/cypresssemiconductorco/psoc6pdl) | Peripheral driver library for PSoC 6 devices. The library is device-independent, so can be precompiled and   used for any PSoC 6 MCU device or project. Included automatically by any BSP   targeting a PSoC 6 device | [API   Reference](https://cypresssemiconductorco.github.io/psoc6pdl/pdl_api_reference_manual/html/index.html) |
| [wifi-host-driver](https://github.com/cypresssemiconductorco/wifi-host-driver) | Driver library for Cypress WLAN devices (CYW43xxx) that   can be easily ported to popular RTOSs such as Amazon FreeRTOS and Mbed OS. The wifi-host-driver is included automatically by board support packages that require this driver (those with CYW43xx devices) | [API   Reference](https://cypresssemiconductorco.github.io/wifi-host-driver/API/index.html) |
| [psoc6cm0p](https://github.com/cypresssemiconductorco/psoc6cm0p) | Prebuilt application images for the Cortex M0+ CPU of a dual-CPU PSoC 6 device. | Repository [readme file](https://github.com/cypresssemiconductorco/psoc6cm0p/blob/master/README.md) |
| [psoc6make](https://github.com/cypresssemiconductorco/psoc6make) | This repository provides the build recipe makefiles and scripts for building and programming PSoC 6 applications. You can build an   application either through a command-line interface (CLI), the ModusToolbox IDE, or a third-party IDE. | Repository [readme file](https://github.com/cypresssemiconductorco/psoc6make/blob/master/README.md) |
| Mbed OS HAL                                                  | Mbed’s hardware abstraction layer. Support for Cypress targets is available from the Mbed OS archive. This HAL is part of the Mbed ecosystem and not provided directly by Cypress. | [Mbed API   documentation](https://os.mbed.com/docs/mbed-os/v5.13/apis/index.html) |

------

## Board Support Packages

The BSP is a central feature of ModusToolbox enablement software. The BSP specifies several critical items for the application, including:

- hardware configuration files for the device (e.g. *design.modus*)
- startup code and linker files for the device
- other libraries that are required to support a kit

BSPs are aligned with Cypress kits; they provide files for basic device functionality. A BSP typically has a *design.modus* file that configures clocks and other board-specific capabilities. That file is used by the ModusToolbox configurators. (See [Configurators and Tools](#_Configurators_and_Tools)). A BSP also includes the required device support code for the device on the board. Users can modify the configuration to suit their application. A BSP uses low-level resources to add functionality. For example, a BSP typically adds the following libraries, as appropriate for the kit/device:

- core-lib – to implement return types and generic functionality useful for any kit
- psoc6hal – to implement the ModusToolbox hardware abstraction layer
- psoc6cm0p – to add a predefined CM0+ application
- psoc6make – to implement the build system infrastructure
- capsense – if appropriate for the kit

Application-specific functionality is added by the starter application makefile. For example, if the example uses the RGB LED on a kit, it will include the rgb-led library in its makefile.

Cypress releases BSPs independently of ModusToolbox software as a whole. This [search link](https://github.com/cypresssemiconductorco?q=TARGET_) finds all currently available BSPs on the Cypress GitHub site.

The search results include links to each repository, named TARGET_*kitnumber*. For example, you will find links to repositories like [TARGET_CY8CPROTO-062-4343W](https://github.com/cypresssemiconductorco/TARGET_CY8CPROTO-062-4343W). Each repository provides links to relevant documentation. The following links use this BSP as an example. Each BSP has its own documentation.

The information provided varies, but typically includes one or more of:

- an [API reference for the BSP](https://cypresssemiconductorco.github.io/TARGET_CY8CPROTO-062-4343W/html/modules.html)
- the [BSP User Guide](https://cypresssemiconductorco.github.io/TARGET_CY8CPROTO-062-4343W/html/md_bsp_mt_bsp_user_guide.html)
- a link to the [associated kit page](https://www.cypress.com/documentation/development-kitsboards/psoc-6-wi-fi-bt-prototyping-kit-cy8cproto-062-4343w) with kit-specific documentation

A BSP is specific to a board and the device on that board. For custom development, you can create or modify a BSP for your device. See the[ BSP User Guide](https://cypresssemiconductorco.github.io/TARGET_CY8CKIT-062-WIFI-BT/html/md_bsp_mt_bsp_user_guide.html) for how BSPs work and how to create your own for a custom board.

## Middleware

The Bluetooth SDK repositories are not yet public, so the link to these repos will give you a 404 error. For now, this gives you an idea of the btsdk capabilities and organization.

| Connectivity    Middleware                                   | Description                                                  | Docs                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [btsdk-audio](https://github.com/cypresssemiconductorco/btsdk-audio) | The Bluetooth SDK is factored into a collection of smaller libraries, so that you can download and use those parts of the SDK necessary for your application. | [btsdk-docs](https://cypresssemiconductorco.github.io/btsdk-docs/BT-SDK/index.html) |
| [btsdk-ble](https://github.com/cypresssemiconductorco/btsdk-ble) | If you use a starter application you don't need to download or install individual libraries. |                                                              |
| [btsdk_drivers](https://github.com/cypresssemiconductorco/btsdk-drivers) | Follow the instructions in the ModusToolbox IDE new application wizard, and in the stand-alone Project Creator to create a local copy of the complete SDK. |                                                              |
| [btsdk-hid](https://github.com/cypresssemiconductorco/btsdk-hid) | The SDK features a dual-mode Bluetooth stack with stack- and   profile-level APIs for embedded BT application development. |                                                              |
| [btsdk-include](https://github.com/cypresssemiconductorco/btsdk-include) | It supports GAP,  GATT, SMP, RFCOMM, SDP, AVDT/AVCT and BLE Mesh protocols, as well as  over-the-air upgrade. |                                                              |
| [btsdk-mesh](https://github.com/cypresssemiconductorco/btsdk-mesh) |                                                              |                                                              |
| [btsdk-ota](https://github.com/cypresssemiconductorco/btsdk-ota) |                                                              |                                                              |
| [btsdk-rfcomm](https://github.com/cypresssemiconductorco/btsdk-rfcomm) |                                                              |                                                              |
| [btsdk-tools](https://github.com/cypresssemiconductorco/btsdk-tools) |                                                              |                                                              |
| [btsdk-utils](https://github.com/cypresssemiconductorco/btsdk-utils) |                                                              |                                                              |
| [btsdk-host-apps-bt-ble](https://github.com/cypresssemiconductorco/btsdk-host-apps-bt-ble) |                                                              |                                                              |
| [btsdk-host-apps-mesh](https://github.com/cypresssemiconductorco/btsdk-host-apps-mesh) |                                                              |                                                              |
| [btsdk-peer-apps-bel](https://github.com/cypresssemiconductorco/btsdk-peer-apps-ble) |                                                              |                                                              |
| [btsdk-peer-apps-mesh](https://github.com/cypresssemiconductorco/btsdk-peer-apps-mesh) |                                                              |                                                              |
| [btsdk-peer-apps-ota](https://github.com/cypresssemiconductorco/btsdk-peer-apps-ota) |                                                              |                                                              |
| [aws-iot](https://github.com/cypresssemiconductorco/aws-iot) | Provides secure, bi-directional communication between Internet-connected devices such as sensors, actuators, embedded micro-controllers, or smart appliances and the AWS Cloud. Supports MQTT and HTTP protocols. | [Developer   Guide](https://docs.aws.amazon.com/iot/latest/developerguide/what-is-aws-iot.html) |
| [enterprise-security](https://github.com/cypresssemiconductorco/enterprise-security) | This library implements a collection of the most commonly used   Extensible Authentication Protocols (EAP) used in enterprise WiFi networks | [API   Reference](https://cypresssemiconductorco.github.io/enterprise-security/api_reference_manual/html/index.html) |
| [http-server](https://github.com/cypresssemiconductorco/http-server) | Provides communication functions for an HTTP server.         | [ReadMe](https://github.com/cypresssemiconductorco/http-server/blob/master/README.md) |
| [connectivity-utilities](https://github.com/cypresssemiconductorco/connectivity-utilities) | General purpose middleware connectivity utilities, for instance a   linked_list or a json_parser | See the code for each                                        |
| [bless](https://github.com/cypresssemiconductorco/bless)     | The Bluetooth Low Energy Subsystem (bless)   library contains a comprehensive API to configure the BLE Stack and the underlying chip hardware. It incorporates a Bluetooth Core Specification v5.0   compliant protocol stack. You may access the GAP, GATT and L2CAP layers of the stack using the API. | [API   Reference](https://cypresssemiconductorco.github.io/bless/ble_api_reference_manual/html/index.html) |
| Arm Mbed Cordio                                              | An open source Bluetooth Low Energy (BLE) solution offering both   host and controller subsystems, with abstraction interfaces for both RTOS and hardware. It is part of the Mbed OS ecosystem and not provided by Cypress. | [Mbed   OS documentation](https://os.mbed.com/docs/mbed-os/latest/apis/bluetooth.html) |
| **PSoC 6 Middleware**                                        | **Description**                                              | **Docs**                                                     |
| [capsense](https://github.com/cypresssemiconductorco/capsense) | Cypress capacitive sensing solution. Capacitive sensing can be used   in a variety of applications and products where conventional mechanical buttons can be replaced with sleek human interfaces to transform the way users interact with electronic systems. | [API   Reference](https://cypresssemiconductorco.github.io/capsense/capsense_api_reference_manual/html/index.html) |
| [csdadc](https://github.com/cypresssemiconductorco/csdadc)   | Enables the ADC functionality of the CapSense Sigma-Delta   hardware block. Useful for devices that do not include other ADC/IDAC options. The CSD HW block enables multiple sensing capabilities on PSoC devices including self-cap and mutual-cap capacitive touch sensing solutions, a 10-bit ADC, IDAC, and Comparator | [API   Reference](https://cypresssemiconductorco.github.io/csdadc/csdadc_api_reference_manual/html/index.html) |
| [csdidac](https://github.com/cypresssemiconductorco/csdidac) | The same, for IDAC functionality.                            | [API   Reference](https://cypresssemiconductorco.github.io/csdidac/csdidac_api_reference_manual/html/index.html) |
| [usbdev](https://github.com/cypresssemiconductorco/usbdev)   | The USB Device library provides a full-speed USB 2.0 Chapter 9   specification compliant device framework. It uses the USBFS driver from PDL. The middleware supports Audio, CDC, and HID, and other classes. Use the USB Configurator tool to construct the USB Device descriptor. | [API   Reference](https://cypresssemiconductorco.github.io/usbdev/usbfs_dev_api_reference_manual/html/index.html) |
| [dfu](https://github.com/cypresssemiconductorco/dfu)         | The Device Firmware Update (DFU) library provides an API for   updating firmware images. You can create an application loader to receive and switch to the new application, and a loadable application to be transferred and programmed. | [API   Reference](https://cypresssemiconductorco.github.io/dfu/dfu_sdk_api_reference_manual/html/index.html) |
| [Secure   Boot SDK](https://github.com/cypresssemiconductorco/cysecuretools) | This SDK includes all required libraries, tools, and sample code to   provision and develop applications for PSoC 64 MCUs. | [User   Guide](https://www.cypress.com/documentation/software-and-drivers/psoc-64-secure-mcu-secure-boot-sdk-user-guide) |
| [emeeprom](https://github.com/cypresssemiconductorco/emeeprom) | The Emulated EEPROM library provides an API to manage an emulated EEPROM in flash. It has support for wear leveling and restoring corrupted data from a redundant copy. | [API   Reference](https://cypresssemiconductorco.github.io/emeeprom/em_eeprom_api_reference_manual/html/index.html) |
| **Other Middleware**                                         | **Description**                                              | **Docs**                                                     |
| [freertos](https://github.com/cypresssemiconductorco/freertos) | FreeRTOS kernel, distributed as standard C source files with   configuration header file, for use with the PSoC 6 MCU. | [FreeRTOS web page](http://www.freertos.org/a00106.html)     |
| [emwin](https://github.com/cypresssemiconductorco/emwin)     | Segger embedded graphic library and graphical user interface (GUI)   framework designed to provide processor- and display controller-independent GUI for any application that needs a graphical display. | [Overview](https://cypresssemiconductorco.github.io/middleware-emwin/emwin_overview/html/index.html) |
| Arm Mbed TLS                                                 | A library to include cryptographic and SSL/TLS capabilities in an   embedded application. It is part of the Mbed OS ecosystem and not provided by Cypress. | [API Reference](https://tls.mbed.org/api/)                   |
| **Tools**                                                    | **Description** (may also be installed by ModusToolbox installer) | **Docs**                                                     |
| [Firmware-loader](https://github.com/cypresssemiconductorco/Firmware-loader) | A command-line tool to update KitProg low-level program/debug communication firmware on Cypress kits | [ReadMe](https://github.com/cypresssemiconductorco/Firmware-loader/blob/master/README.md) |
| [cype](https://github.com/cypresssemiconductorco/cype)       | Cypress Power Estimator (CyPE) library provides software based estimation of power consumption on Cypress kits. This library should be used in conjunction with the Power Estimator tool available in ModusToolbox 2.0 IDE | [ReadMe](https://github.com/cypresssemiconductorco/cype/blob/master/README.md) |


