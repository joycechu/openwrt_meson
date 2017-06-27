#
# Copyright (C) 2017 Stijn Tintel <stijn@linux-ipv6.be>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=fiptool

PKG_SOURCE_URL=https://github.com/hardkernel/u-boot.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2016-06-01
PKG_SOURCE_VERSION:=3a2dd09540d3639671d86145336f400ec07b1a4e

PKG_LICENSE:=BSD-3-Clause

include $(INCLUDE_DIR)/host-build.mk

define Host/Compile
	+$(HOST_MAKE_VARS) \
	$(MAKE) $(HOST_JOBS) -C $(HOST_BUILD_DIR)/tools/fip_create \
		$(HOST_MAKE_FLAGS) \
		$(1)
endef

define Host/Install
	$(INSTALL_BIN) \
		$(HOST_BUILD_DIR)/tools/fip_create/fip_create \
		$(STAGING_DIR_HOST)/bin/
endef

define Host/Clean
	rm -f $(STAGING_DIR_HOST)/bin/fip_create
endef

$(eval $(call HostBuild))
