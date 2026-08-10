# SPDX-License-Identifier: GPL-2.0-only

include $(TOPDIR)/rules.mk

ARCH:=arm
BOARD:=zx279128
BOARDNAME:=ZTE ZX279128S
SUBTARGETS:=generic
CPU_TYPE:=cortex-a9
FEATURES:=ramdisk squashfs
KERNEL_PATCHVER:=6.12

include $(INCLUDE_DIR)/target.mk

KERNELNAME:=zImage dtbs

DEFAULT_PACKAGES += \
	kmod-gpio-button-hotplug \
	kmod-mtd-rw

$(eval $(call BuildTarget))
