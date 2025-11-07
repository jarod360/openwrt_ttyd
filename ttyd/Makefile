#
# Copyright (C) 2025 Jarod
# Modified OpenWrt Makefile for ttyd with TLS/SSL support
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ttyd
PKG_VERSION:=1.7.7
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/tsl0922/ttyd/tar.gz/refs/tags/$(PKG_VERSION)?
PKG_HASH:=skip

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Jarod <jarod@example.com>

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=libwebsockets-full/host

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/ttyd
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Terminal
  TITLE:=ttyd - Web-based terminal with SSL/TLS
  URL:=https://github.com/tsl0922/ttyd
  DEPENDS:=+libjson-c +libopenssl +libwebsockets-full
endef

define Package/ttyd/description
ttyd is a simple command-line tool for sharing a terminal over the web,
built on top of libwebsockets. This version enables SSL/TLS support
so you can use HTTPS (wss://) directly.
endef

CMAKE_OPTIONS += \
	-DSSL_SUPPORT=ON \
	-DOPENSSL_ROOT_DIR=$(STAGING_DIR)/usr \
	-DLWS_WITH_SSL=ON \
	-DLWS_WITH_MBEDTLS=OFF \
	-DLWS_WITHOUT_EXTENSIONS=OFF

define Package/ttyd/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ttyd $(1)/usr/bin/
endef

$(eval $(call BuildPackage,ttyd))
