#
# Copyright (C) 2011-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libjwt
PKG_VERSION:=1.10.0
PKG_RELEASE:=1
PKG_LICENSE:=MIT

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://github.com/benmcollins/libjwt/releases
PKG_HASH:=783132e2fc970feefc2fa54199ef65ee020bd8e0e991a78ea44b8586353a0947

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/jansson
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=JWT library
  URL:=https://github.com/benmcollins/libjwt
  MAINTAINER:=ben collins
endef

define Package/jansson/description
  JWT library for C
endef

TARGET_CFLAGS += $(FPIC)
TARGET_LDFLAGS += -Wl,-rpath-link=$(STAGING_DIR)/usr/lib -lm

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib,include}
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libjwt* $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
endef

define Package/jansson/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libjwt*so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libjwt))
