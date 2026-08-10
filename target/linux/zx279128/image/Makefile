# SPDX-License-Identifier: GPL-2.0-only

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

define Device/zte_e2631
  DEVICE_VENDOR := ZTE
  DEVICE_MODEL := E2631
  DEVICE_DTS := zx279128s-e2631
  DEVICE_DTS_DIR := $(DTS_DIR)/zte
  KERNEL_NAME := zImage
  KERNEL_LOADADDR := 0x40008000
  KERNEL_ENTRY := 0x40008000
  KERNEL := kernel-bin | append-dtb | uImage none
  KERNEL_INITRAMFS := kernel-bin | append-dtb | uImage none
  KERNEL_INITRAMFS_SUFFIX := -uImage
  IMAGES :=
  DEVICE_PACKAGES :=
endef
TARGET_DEVICES += zte_e2631

$(eval $(call BuildImage))
