# Smallstep for Desktops

Smallstep helps ensure that access to financial data, code repositories, PII and other sensitive resources is only possible from trusted, company-managed devices.

## System Requirements

### Windows

- Windows 10 or later
- Trusted Platform Module (TPM 2.0)

### Linux

- Flatpak, or Debian 12+, Ubuntu 22.04+, Fedora 38+
- `systemd`-based service manager
- Trusted Platform Module (TPM 2.0)
- p11-kit
- tpm-tss2

### macOS

- macOS 13 (Ventura) or later
- Secure Enclave

## Runtime Requirements

All platforms require an internet connection for normal operation.

### Windows

- *Administrator privileges* - the Smallstep app requires privilege escalation to be able to communicate to the TPM

### macOS

- *Location permission* - to enable management of Wifi networks, the Smallstep app needs location permission
- *Keychain access* - the Smallstep app uses the macOS keychain to store both keys and certificates it manages
- *Network Extension entitlement* - the Smallstep app requests the *Network Extension* entitlement so that it can manage VPN connections

### Linux

- *TPM read/write permission* - the Smallstep app communicates to the TPM from user-space using `tpm-tss2`, and the running user must have read/write permissions to the TPM resource manager (typically `/dev/tpmrm0`)

On all platforms, the Smallstep app manages a directory on the filesystem in well-known location for management of keys and certificates:

- On macOS: `$HOME/Library/Application Support/Smallstep`
- On Windows: `%LOCALAPPDATA%/Smallstep`
- On Linux: `$XDG_RUNTIME_DIR/step-agent` and `$XDG_CONFIG_HOME/step-agent`

## Download

Installers for macOS, Windows and Linux can be downloaded from [GitHub releases](https://github.com/smallstep/smallstep-desktop/releases). Releases are signed with, and can be verified, by cosign.

| Platform  | Release  |
|:--|:--|
| macOS  | <a href='https://packages.smallstep.com/stable/darwin/Smallstep.dmg'>Latest Version</a>  |
| Linux (Flatpak) | <a href='https://packages.smallstep.com/stable/flatpak/Smallstep.flatpakref'>Latest Version</a>  |
| Linux (.deb) | <a href='https://packages.smallstep.com/stable/deb/smallstep-desktop.deb'>Latest Version</a>  |
| Linux (.rpm) | <a href='https://packages.smallstep.com/stable/deb/smallstep-desktop.rpm'>Latest Version</a>  |
| Windows  | <a href='https://packages.smallstep.com/stable/windows/Smallstep.exe'>Latest Version</a>  |

## Telemetry

The Smallstep app collects and reports some data from the host device as part of its normal operation. These are:

- Device Identifiers from TPM-enabled platforms
- Device/Computer Name
- Device/Computer Hostname
- Chipset Architecture
- Operating System Version
- WAN IP Address
