# rknpu-driver-dkms

DKMS linux kernel driver for Rockchip RK3588 Series and RK3576 Series NPUs.

WIP! The driver does not compile currently. Please help me to make this a thing!

## Development log

- Copied GPL-2.0 rknpu-0.9.8 driver code from https://github.com/airockchip/rknn-llm
- Makefile changes and added dkms.conf
- Changed includes to local ones were applicable:
- Copied governor.h from 6.11.6 Armbian Linux source code with Rockchip patches.
- Added rockchip_iommu.h rockchip_ipa.h rockchip_opp_select.h rockchip_system_monitor.h from Rockchip Linux Kernel, as these includes are referenced in the driver, but aren't in Armbians patched kernel source.
- .c functions from the headers above have not been included yet, resulting in compile errors.
