#
# Copyright (C) 2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=uboot-meson
PKG_RELEASE:=1
PKG_SOURCE_VERSION:=f1ee03e3f7547d03e1478cc1fc967a9e5a121d92
PKG_BUILD_DIR:=$(KERNEL_BUILD_DIR)/$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/endlessm/u-boot-meson.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_MD5SUM:=
PKG_TARGETS:=bin
QUILT:=1
include $(INCLUDE_DIR)/package.mk

define uboot/m3_f16_no_video_v1
  TITLE:=U-boot for meson3 f16 without video
endef

define uboot/m8b_m200_1G
  TITLE:=U-boot for meson8b m200
endef

define uboot/m8b_m201_1G
  TITLE:=U-boot for meson8b m201
endef

define uboot/m8_k200_v1
  TITLE:=U-boot for meson8 k200
endef

define uboot/m8m2_n200_v1
  TITLE:=U-boot for meson8 k200
endef

define uboot/m6_mbx_v2
  TITLE:=U-boot for meson8 k200
endef

define uboot/m6_dongle_g35_v1
  TITLE:=U-boot for meson8 k200
endef

define uboot/Default
  TITLE:=
  CONFIG:=
  IMAGE:=
endef

UBOOTS:= \
	m3_f16_no_video_v1 \
	m8b_m200_1G \
	m8b_m201_1G \
	m8_k200_v1 \
	m8m2_n200_v1 \
	m6_mbx_v2 \
	m6_dongle_g35_v1

define Package/uboot/template
define Package/uboot-meson-$(1)
  SECTION:=boot
  CATEGORY:=Boot Loaders
  TITLE:=$(2)
  DEPENDS:=@TARGET_mesongx
  URL:=http://www.denx.de/wiki/U-Boot
  VARIANT:=$(1)
endef
endef

define BuildUbootPackage
	$(eval $(uboot/Default))
	$(eval $(uboot/$(1)))
	$(call Package/uboot/template,$(1),$(TITLE))
endef

ifdef BUILD_VARIANT
$(eval $(call uboot/$(BUILD_VARIANT)))
UBOOT_CONFIG:=$(if $(CONFIG),$(CONFIG),$(BUILD_VARIANT))
UBOOT_IMAGE:=$(if $(IMAGE),$(IMAGE),openwrt-$(BOARD)-$(BUILD_VARIANT)-u-boot.bin)
endif

define Build/Prepare
	$(call Build/Prepare/Default)
	find $(PKG_BUILD_DIR) -name .svn | $(XARGS) rm -rf
endef

define Build/Configure
	$(MAKE) -C $(PKG_BUILD_DIR) \
		$(UBOOT_CONFIG)_config
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) CROSS_COMPILE=$(TARGET_CROSS) 
endef

define Package/uboot/install/template
define Package/uboot-meson-$(1)/install
	$(INSTALL_DIR) $$(1)
	$(CP) $(PKG_BUILD_DIR)/build/u-boot.bin $(BIN_DIR)/$(2)
endef
endef

$(foreach u,$(UBOOTS), \
	$(eval $(call Package/uboot/install/template,$(u),openwrt-$(BOARD)-$(SUBTARGET)-$(u)-u-boot.bin)) \
)

$(foreach u,$(UBOOTS), \
	$(eval $(call BuildUbootPackage,$(u))) \
	$(eval $(call BuildPackage,uboot-meson-$(u))) \
)
