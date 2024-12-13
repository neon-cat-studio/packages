# OpenWRT Package Makefile for Meson
#
# SPDX-License-Identifier: Apache-2.0

include $(TOPDIR)/rules.mk

PKG_NAME:=meson
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/mesonbuild/meson/releases/download/$(PKG_VERSION)
PKG_HASH:=skip

PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=COPYING

HOST_BUILD_DEPENDS:=ninja/host python3/host

include $(INCLUDE_DIR)/host-build.mk

define Host/Prepare
	$(call Host/Prepare/Default)
endef

define Host/Configure
	$(call Host/Configure/Default)
endef

define Host/Compile
	$(call Host/Compile/Default)
endef

# Install Meson and fix interpreter for Python3
define Host/Install
	$(INSTALL_DIR) $(STAGING_DIR_HOST)/bin
	$(CP) $(HOST_BUILD_DIR)/meson.py $(STAGING_DIR_HOST)/bin/meson
	$(SED) '1s:.*:#!/usr/bin/env python3:' $(STAGING_DIR_HOST)/bin/meson
	chmod +x $(STAGING_DIR_HOST)/bin/meson
endef

define Host/Clean
	$(call Host/Clean/Default)
endef

$(eval $(call HostBuild))
