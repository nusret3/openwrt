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

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/benmcollins/libjwt/archive/
PKG_HASH:=93b399f829cde5f5a232612fcb2909d63e7a9530bcaef40491a0493ba1606565


PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libjwt
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=JWT library
  URL:=https://github.com/benmcollins/libjwt
  MAINTAINER:=ben collins
endef

define Package/libjwt/description
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

define Package/libjwt/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libjwt*so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libjwt))
