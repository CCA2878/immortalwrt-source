# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2006-2011 OpenWrt.org

include $(TOPDIR)/rules.mk

ARCH:=i386
BOARD:=x86
BOARDNAME:=x86
FEATURES:=squashfs ext4 vdi vmdk pcmcia targz fpu boot-part rootfs-part
SUBTARGETS:=64 generic zen legacy geode 
MAINTAINER:=Felix Fietkau <nbd@nbd.name>

KERNEL_PATCHVER:=5.4
KERNEL_TESTING_PATCHVER:=5.10

KERNELNAME:=bzImage

include $(INCLUDE_DIR)/target.mk

DEFAULT_PACKAGES += partx-utils mkf2fs fdisk e2fsprogs kmod-usb-hid kmod-e1000e kmod-igb kmod-igbvf \
		    kmod-ixgbe kmod-pcnet32 kmod-tulip kmod-vmxnet3 kmod-i40e kmod-iavf kmod-r8125 \
		    kmod-r8168 kmod-8139cp kmod-8139too kmod-fs-f2fs autocore-x86 automount \
		    kmod-sound-hda-core kmod-sound-hda-codec-realtek kmod-sound-hda-codec-via \
		    kmod-sound-via82xx kmod-sound-hda-intel kmod-sound-hda-codec-hdmi kmod-sound-i8x0 \
		    kmod-usb-audio kmod-usb-net kmod-usb-net-asix kmod-usb-net-asix-ax88179 \
		    kmod-usb-net-rtl8150 kmod-usb-net-rtl8152 kmod-mlx4-core kmod-mlx5-core

$(eval $(call BuildTarget))

$(eval $(call $(if $(CONFIG_ISO_IMAGES),SetupHostCommand,Ignore),mkisofs, \
	Please install mkisofs. , \
	mkisofs -v 2>&1 , \
	genisoimage -v 2>&1 | grep genisoimage, \
	xorrisofs -v 2>&1 | grep xorriso \
))
