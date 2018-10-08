#
# Copyright (C) 2017 Stijn Tintel <stijn@linux-ipv6.be>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=odroid-firmware
PKG_VERSION:=2017-02-24
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/hardkernel/u-boot.git
PKG_SOURCE_VERSION:=205c7b3259559283161703a1a200b787c2c445a5
PKG_MIRROR_HASH:=

PKG_MAINTAINER:=Stijn Tintel <stijn@linux-ipv6.be>

PKG_FLAGS:=nonshared

include $(INCLUDE_DIR)/package.mk

define Package/odroid-firmware-c2
  SECTION:=firmware
  CATEGORY:=Firmware
  TITLE:=Odroid C2 firmware
  DEPENDS:=@TARGET_mesongx
endef

define Build/Compile

endef

define Package/odroid-firmware-c2/install
	$(INSTALL_DIR) $(STAGING_DIR_IMAGE)/odroidc2
	$(CP) \
		$(PKG_BUILD_DIR)/fip/gxb/*.{bin,package} \
		$(STAGING_DIR_IMAGE)/odroidc2
	$(CP) \
		$(PKG_BUILD_DIR)/sd_fuse/bl1.bin.hardkernel \
		$(STAGING_DIR_IMAGE)/odroidc2
endef

$(eval $(call BuildPackage,odroid-firmware-c2))
