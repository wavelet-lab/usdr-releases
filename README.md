# uSDR Releases

This repository provides official prebuilt packages for uSDR software and
related components.

Package availability, supported Ubuntu releases, architectures, and licensing
terms may vary between components. See the notes attached to each release for
details.

## Available packages

### libcapi79xx

`libcapi79xx` is a proprietary Wavelet Lab runtime library that provides
AFE79xx hardware support to uSDR applications. It is a required runtime
dependency of DSDR, which cannot operate without it.

#### Supported systems

- Ubuntu 20.04 Focal
- Ubuntu 22.04 Jammy
- Ubuntu 24.04 Noble
- Ubuntu 26.04 Resolute
- AMD64 and ARM64 architectures

## Download

Packages are available on the
[Releases](https://github.com/wavelet-lab/usdr-releases/releases) page.

Select the required package and download the `.deb` file matching both the
Ubuntu release and the architecture of the target system.

Determine the Ubuntu codename:

```bash
. /etc/os-release
echo "$VERSION_CODENAME"
```

Determine the architecture:

```bash
dpkg --print-architecture
```

The GitHub-generated `Source code` archives do not contain the distributed
binary packages. Download the appropriate `.deb` file from the release assets.

## Installing libcapi79xx

### Dependencies

`libcapi79xx` depends on the uSDR library. Add the Wavelet Lab PPA before
installing the package:

```bash
sudo add-apt-repository ppa:wavelet-lab/usdr-lib
sudo apt update
```

### Verification

Each package has a corresponding `.sha256` file. For example:

```bash
sha256sum --check libcapi79xx_1.0.1~resolute0_amd64.deb.sha256
```

Do not install a package if checksum verification fails.

### Installation

Install the downloaded package using APT. For example:

```bash
sudo dpkg -i libcapi79xx_1.0.1~resolute0_amd64.deb
```

APT will install the required dependencies automatically. Restart DSDR after
installing or upgrading the library.

### Custom library and configuration paths

DSDR automatically uses the library and reference configuration files
installed by the package. Custom locations can still be selected when
necessary:

```bash
export AFECAPI=/custom/path/libcapi79xx.so
export AFECFG_PATH=/custom/path/refs
```

Unset these variables to restore the package defaults:

```bash
unset AFECAPI
unset AFECFG_PATH
```

## Licensing

Each package is distributed under the terms stated in its release notes and
included license information.

`libcapi79xx` is proprietary and confidential Wavelet Lab software.

Unauthorized copying, modification, distribution, sublicensing, or use is
prohibited without prior written permission from Wavelet Lab.
