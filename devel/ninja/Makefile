# OpenWRT Package Makefile for Ninja (Host Tool)
#
# SPDX-License-Identifier: Apache-2.0

include $(TOPDIR)/rules.mk

PKG_NAME:=ninja
PKG_VERSION:=1.11.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/Kitware/ninja.git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_HASH:=skip

PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=COPYING

HOST_BUILD_DEPENDS:=cmake/host

include $(INCLUDE_DIR)/host-build.mk

define Host/Prepare
	$(call Host/Prepare/Default)
endef

define Host/Configure
	$(call Host/Configure/Default)
endef

define Host/Compile
	$(MAKE) -C $(HOST_BUILD_DIR) \
		CXX="$(HOSTCXX)" \
		CC="$(HOSTCC)" \
		CFLAGS="$(HOST_CFLAGS)" \
		LDFLAGS="$(HOST_LDFLAGS)"
endef

define Host/Install
	$(INSTALL_DIR) $(STAGING_DIR_HOST)/bin
	$(INSTALL_BIN) $(HOST_BUILD_DIR)/ninja $(STAGING_DIR_HOST)/bin/ninja
endef

define Host/Clean
	$(call Host/Clean/Default)
endef

$(eval $(call HostBuild))
