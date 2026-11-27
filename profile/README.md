# Valparaiso OS

Valparaiso OS is an illumos desktop operating system built on OpenIndiana with KDE Plasma. It includes a live desktop, a graphical installer, and tools for writing, development, and container workloads.

**Developer preview.** This build may contain bugs. We recommend testing in a virtual machine. If you test on physical hardware, use a wired Ethernet connection.

## Try the preview

- [Download the x86-64 QA ISO and its SHA-256 checksum](https://valparaiso-os.tech/#download)
- [Create a bootable live USB](https://valparaiso-os.tech/docs/#live-usb)
- [Attach the ISO and boot in a VM](https://valparaiso-os.tech/docs/#virtual-machine)
- [See screenshots from QA builds](https://valparaiso-os.tech/#screenshots)
- [Report a bug or suggest an improvement](https://github.com/Valparaiso-OS/feedback/issues)

For VM testing, start with 8 GiB of RAM and an 80 GiB blank virtual disk. To try the live desktop, boot the ISO as a virtual optical drive. To install, open **Install Valparaiso** and select a dedicated blank target disk.

## What’s included

- **LibreOffice** with Writer, Calc, and Impress. Ask Dodie provides on-device writing help in Writer.
- **Valpo Files, Pak Center, and Valpo Analytics** for browsing files, exploring IPS packages, and opening sample workbooks.
- **Valpo Code and Valpo Containers** for development, browsing Podman images, and viewing the host’s illumos zone inventory.

![Valpo Files browsing the home folder on the Valparaiso QA desktop](https://valparaiso-os.tech/assets/valpo-files.webp)

*Actual screenshot of Valpo Files on Valparaiso. This QA build offers filename and full-text indexing options. Semantic search is unavailable in this build.*

## What sets Valparaiso apart

Valparaiso builds on OpenIndiana and illumos, carrying forward native ZFS storage, zones, and IPS package management. It brings those foundations into a KDE Plasma desktop with a graphical live installer, Valpo apps, and on-device writing help in LibreOffice Writer.

Valpo Containers brings the host’s illumos zone inventory and Podman workloads in a bundled Fedora guest into one desktop app. Valparaiso also configures illumos process hardening during installation and is testing signed UEFI boot in controlled QA configurations.

## Desktop and command line

The graphical installer and desktop apps cover most everyday tasks. If you prefer a shell, open Konsole. Valparaiso retains the OpenIndiana/illumos command-line environment, including native tools for IPS packages, ZFS, and zones.

![Fastfetch in Konsole showing OpenIndiana, SunOS, and KDE Plasma system details](https://valparaiso-os.tech/assets/fastfetch.webp)

*Actual screenshot of Fastfetch in Konsole on an installed Valparaiso QA VM.*

## Current QA status

The November 26, 2026 image passed offline live-boot checks, including Containers background startup and listing the native global zone. Fresh-install testing and non-global zone lifecycle testing remain open for this exact image. Physical hardware support varies, and Secure Boot compatibility remains unverified for this preview.

## Platform security

- **Process hardening.** The graphical and manual installers configure address space layout randomization (ASLR), non-executable stacks, and null-page mapping protection through illumos SMF. An installed QA guest retained all three settings after reboot, and LightDM and the Plasma session inherited them. See the [security roadmap](https://github.com/Valparaiso-OS/Valparaiso/blob/main/docs/security-roadmap.md).
- **UEFI Secure Boot.** Valparaiso can produce a signed x86-64 EFI installer for testing with enrolled QA keys. In an enforced OVMF VM, the signed image reached the graphical installer and firmware rejected unsigned and modified loaders. This validation applies to the signed QA configuration. Compatibility for the public preview ISO and installed systems still needs qualification. See [Secure Boot QA](https://github.com/Valparaiso-OS/Valparaiso/blob/main/docs/secure-boot.md).
- **TPM 2.0.** Firmware communication was demonstrated in a test VM. The tested OpenIndiana guest exposed no usable TPM CRB or TIS device interface. Measured boot and TPM-sealed disk unlock remain open. See the [security roadmap](https://github.com/Valparaiso-OS/Valparaiso/blob/main/docs/security-roadmap.md).
- **Post-quantum boot verification.** A standalone UEFI QA probe verified an ML-DSA-65 boot manifest and rejected a modified manifest and a changed configuration file. Full boot-chain enforcement remains experimental. See the [ML-DSA-65 prototype](https://github.com/Valparaiso-OS/Valparaiso/blob/main/docs/secure-boot.md#ml-dsa-65-boot-manifest-prototype).

- **Containers LAN publishing demo.** The Fedora guest uses restricted QEMU user networking. HTTP listens only on loopback. LAN publishing requires a separate TLS 1.3 listener on an explicitly approved interface. The desktop administrator supplies a certificate trusted by clients and valid for the host address, plus its matching private key.

## Project documentation

The technical documents below require access to the Valparaiso repository. The [public installation guide](https://valparaiso-os.tech/docs/) is available to everyone.

- [Graphical installer](https://github.com/Valparaiso-OS/Valparaiso/blob/main/docs/graphical-installer.md)
- [Security roadmap](https://github.com/Valparaiso-OS/Valparaiso/blob/main/docs/security-roadmap.md)

Valparaiso OS is dedicated to D. Pauline “Dodie” Williams. [Read about Dodie and the project](https://valparaiso-os.tech/#dodie).
