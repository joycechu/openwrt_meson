#
# Copyright (C) 2017 Stijn Tintel <stijn@linux-ipv6.be>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=meson-tools
PKG_VERSION:=0.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_HASH:=f1bd619368075186b742af84a02a83f60ffba2e6da67433abbe6e6d5c77373cb
PKG_SOURCE_URL:=https://github.com/afaerber/meson-tools/archive/v$(PKG_VERSION)

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/kernel.mk

define Host/Install
	$(INSTALL_BIN) $(HOST_BUILD_DIR)/amlbootsig $(STAGING_DIR_HOST)/bin/
endef

define Host/Clean
	rm -f $(STAGING_DIR_HOST)/bin/amlbootsig
endef

$(eval $(call HostBuild))
