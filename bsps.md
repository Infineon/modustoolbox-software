# Board support packages

For any ModusToolbox™ application, you must specify a Board Support Package (BSP), which defines basic device features and capabilities. The BSP is a central feature of ModusToolbox™ software. The BSP specifies several critical items for the application, including:

- hardware configuration files for the device (for example, *design.modus*)
- startup code and linker files for the device
- other libraries that are required to support a kit

BSPs are aligned with our kits; they provide files for basic device functionality. A BSP typically has a *design.modus* file that configures clocks and other board-specific capabilities. That file is used by the ModusToolbox™ configurators. A BSP also includes the required device support code for the device on the board. You can modify the configuration to suit your application. 

We release BSPs independently of the Tools package. This [search link](https://github.com/Infineon?q=TARGET_) finds all currently available BSPs on the GitHub site. Use the Project Creator available in the ModusToolbox Base Tools package to create the projects with the specific BSPs (get from [main website](https://www.infineon.com/cms/en/design-support/tools/sdk/modustoolbox-software)).

The search results include links to each repository, named TARGET_*kitnumber*. For example, you will find links to repositories like [TARGET_CY8CPROTO-062-4343W](https://github.com/Infineon/TARGET_CY8CPROTO-062-4343W). Each repository provides links to relevant documentation. The following links use this BSP as an example. Each BSP has its own documentation.

The information provided varies, but typically includes one or more of:

- an [API reference for the BSP](https://infineon.github.io/TARGET_CY8CPROTO-062-4343W/html/modules.html)
- the [BSP overview](https://infineon.github.io/TARGET_CY8CPROTO-062-4343W/html/md_source_bsps_mt_bsp_user_guide.html)
- a link to the [associated kit page](https://www.cypress.com/documentation/development-kitsboards/psoc-6-wi-fi-bt-prototyping-kit-cy8cproto-062-4343w) with kit-specific documentation

A BSP is specific to a board and the device on that board. For custom development, you can create or modify a BSP for your device. See the [ModusToolbox™ BSP Assistant user guide](http://www.Infineon.com/ModusToolboxBSPAssistant) for how they work and how to create your own for a custom board.
