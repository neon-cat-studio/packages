# OpenWRT Package Makefile for meson-tools (Host Tool)
#
# SPDX-License-Identifier: GPL-2.0+

include $(TOPDIR)/rules.mk

PKG_NAME:=meson-tools
PKG_VERSION:=0a02e2d34413f4bf9b15946352bc8c8ee13a5843
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/afaerber/meson-tools.git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_HASH:=skip

PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=COPYING

HOST_BUILD_DEPENDS:=openssl/host

include $(INCLUDE_DIR)/host-build.mk

HOST_MESON_TOOLS_PROGS:=amlbootsig unamlbootsig amlinfo

define Host/Prepare
	$(call Host/Prepare/Default)
endef

define Host/Compile
	$(MAKE) -C $(HOST_BUILD_DIR) \
		CC="$(HOSTCC)" \
		CFLAGS="$(HOST_CFLAGS)" \
		LDFLAGS="$(HOST_LDFLAGS) -lssl -lcrypto"
endef

define Host/Install
	$(INSTALL_DIR) $(STAGING_DIR_HOST)/bin
	$(foreach prog,$(HOST_MESON_TOOLS_PROGS), \
		$(INSTALL_BIN) $(HOST_BUILD_DIR)/$(prog) $(STAGING_DIR_HOST)/bin/$(prog))
endef

define Host/Clean
	$(call Host/Clean/Default)
endef

$(eval $(call HostBuild))
