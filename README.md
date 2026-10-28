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
```

## How to build (Yocto vanilla)

At the time of writing, we do not have a repo manifest setup.
Follow these instructions to create a standard Yocto 6 environment:

```
# Clone the Yocto repositories
git clone -b yocto-6.0.4 https://git.openembedded.org/bitbake bitbake
git clone -b yocto-6.0.4 https://git.openembedded.org/openembedded-core
git clone -b yocto-6.0.4 https://git.yoctoproject.org/meta-yocto
# Clone this meta layer
git clone https://github.com/rdkcentral/meta-rdkb-bsp

# Setup bitbake
source openembedded-core/oe-init-build-env

# After the "source" above, you will be in the newly created
# "build" working directory

# Edit bblayers.conf and add the full path of meta-rdkb-bsp
# (readlink -f ../meta-rdkb-bsp)
vi conf/bblayers.conf

# Edit local.conf and set MACHINE="armefi64"
vi conf/local.conf

# Enable passwordless root login (for development use only)
bitbake-config-build enable-fragment core/yocto/root-login-with-empty-password

# Build core image base
bitbake core-image-base

# Use Yocto's runqemu tool
runqemu nographic snapshot
```

(Refer to the [Yocto Developer Manual](https://docs.yoctoproject.org/6.0/dev-manual/poky-manual-setup.html) for the upstream guide)
