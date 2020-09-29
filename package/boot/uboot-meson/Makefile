#
# Copyright (C) 2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_RELEASE:=1
PKG_SOURCE_VERSION:=f1ee03e3f7547d03e1478cc1fc967a9e5a121d92
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/endlessm/u-boot-meson.git

include $(INCLUDE_DIR)/u-boot.mk
include $(INCLUDE_DIR)/package.mk

define U-Boot/Default
  BUILD_TARGET:=mesongx
  UBOOT_IMAGE:=build/u-boot.bin
  HIDDEN:=1
endef

define U-Boot/m3_f16_no_video_v1
  NAME:=U-boot for meson3 f16 without video
  BUILD_DEVICES:=m3_f16_no_video_v1
endef

define U-Boot/m8b_m200_1G
  NAME:=U-boot for meson8b m200
  BUILD_DEVICES:=m8b_m200_1G
endef

define U-Boot/m8b_m201_1G
  NAME:=U-boot for meson8b m201
  BUILD_DEVICES:=m8b_m201_1G
endef

define U-Boot/m8_k200_v1
  NAME:=U-boot for meson8 k200
  BUILD_DEVICES:=m8_k200_v1
endef

define U-Boot/m8m2_n200_v1
  NAME:=U-boot for meson8 k200
  BUILD_DEVICES:=m8m2_n200_v1
endef

define U-Boot/m6_mbx_v2
  NAME:=U-boot for meson8 k200
  BUILD_DEVICES:=m6_mbx_v2
endef

define U-Boot/m6_dongle_g35_v1
  NAME:=U-boot for meson8 k200
  BUILD_DEVICES:=m6_dongle_g35_v1
endef

UBOOT_MAKE_FLAGS :=

UBOOT_TARGETS := \
	m3_f16_no_video_v1 \
	m8b_m200_1G \
	m8b_m201_1G \
	m8_k200_v1 \
	m8m2_n200_v1 \
	m6_mbx_v2 \
	m6_dongle_g35_v1


define Build/Prepare
	$(call Build/Prepare/Default)
	find $(PKG_BUILD_DIR) -name .svn | $(XARGS) rm -rf
endef

$(eval $(call BuildPackage/U-Boot))
