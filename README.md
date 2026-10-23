# meta-rdkb-bsp

`meta-rdkb-bsp` is a Yocto Project / OpenEmbedded layer containing BSP metadata for ARM-based platforms targeting RDK-B broadband devices.

The layer provides platform-specific configuration and integration required to build RDK-B images for supported ARM hardware.

## Scope

This layer may contain:

- Machine configurations
- BSP-specific recipes
- Kernel configuration and patches
- Bootloader configuration
- Device tree integration
- Firmware and hardware-specific dependencies
- Platform-specific overrides and configuration

The goal is to keep hardware and BSP-specific metadata separated from the RDK-B runtime and application layers.

## Supported Platforms

The layer is intended to support multiple ARM SoCs and reference platforms used for broadband gateways and networking devices.

Platform support will be added under the appropriate machine and BSP-specific directories.

## Layer Structure

Typical contents include:

```text
meta-rdkb-bsp/
├── conf/
│   ├── layer.conf
│   └── machine/
├── recipes-bsp/
├── recipes-kernel/
└── recipes-support/
