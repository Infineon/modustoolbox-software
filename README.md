# ModusToolbox™ software

ModusToolbox™ software is a modern, extensible development environment supporting a wide range of Infineon microcontroller devices. It provides a flexible set of tools and a diverse, high-quality collection of application-focused software. These include configuration tools, low-level drivers, libraries, and operating system support, most of which are compatible with Linux, macOS, and Windows-hosted environments. 

This page helps you identify and find the ModusToolbox™ resources available. These resources are grouped in the following top-level categories:

- [Tools](#tools)
- [Code examples](https://github.com/Infineon/Code-Examples-for-ModusToolbox-Software) (link to separate page)
- [Board support packages](#board-support-packages)
- [Libraries](#libraries)
- [Training material](https://github.com/Infineon/training-modustoolbox) (link to separate page)

## Tools

The [ModusToolbox™ tools package installer](https://www.infineon.com/cms/en/design-support/tools/sdk/modustoolbox-software/) provides various multi-platform development tools to help you work in your preferred flow. The installer includes a make-based build system, Eclipse IDE, configurators, stand-alone project creator and library manager, as well as support for using other IDEs, generating code, compiling, programming, and debugging. Refer to the [ModusToolbox™ tools package user guide](https://www.Infineon.com/ModusToolboxUserGuide) for complete details.

Some tools are available separately on GitHub, including:

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


## Libraries

There are many other parts of ModusToolbox™ software that are provided as libraries. When you create a ModusToolbox™ application, the system downloads all the libraries your application needs to take full advantage of the various features of our devices. A ModusToolbox™ application can use different libraries based on the Active BSP. 

Refer to the [ModusToolbox™ run-time software reference guide](https://www.infineon.com/ModusToolboxRuntimeSoftwareReferenceGuide) for details about the libraries available.
