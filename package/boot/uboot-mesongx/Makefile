#
# Copyright (C) 2017-2019 Stijn Tintel <stijn@linux-ipv6.be>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_VERSION:=2018.11
PKG_RELEASE:=1

PKG_HASH:=737c93f2ea03fec669e840dbee32bcf6238e6924ff5f20e4f1c472ee24e5d37e

include $(INCLUDE_DIR)/u-boot.mk
include $(INCLUDE_DIR)/package.mk

define U-Boot/Default
  ARCH:=arm
  BUILD_TARGET:=mesongx
  HIDDEN:=1
endef

define U-Boot/odroid-c2
  TITLE:=ODROID C2
  BUILD_DEVICES:=odroid-c2
endef

UBOOT_TARGETS:= \
	odroid-c2

$(eval $(call BuildPackage/U-Boot))
