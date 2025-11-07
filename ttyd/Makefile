#
# Copyright (C)
# Licensed under GPLv2
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ttyd
PKG_VERSION:=1.7.4
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/tsl0922/ttyd/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=skip

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=tsl0922 <contact@tsl0922.me>

PKG_BUILD_DEPENDS:=libwebsockets-full
CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += \
	-DUSE_OPENSSL=ON \
	-DLWS_WITH_SSL=ON \
	-DLWS_OPENSSL_CLIENT_CERTS=/etc/ssl/certs \
	-DLWS_DIR=$(STAGING_DIR)/usr \
	-DLWS_LIBRARY_DIRS=$(STAGING_DIR)/usr/lib \
	-DLWS_INCLUDE_DIRS=$(STAGING_DIR)/usr/include \
	-DENABLE_SSL=ON

define Package/ttyd
  SECTION:=net
  CATEGORY:=Network
  TITLE:=ttyd - Web terminal with HTTPS support
  DEPENDS:=+libwebsockets-full +libopenssl +libpthread +zlib
  URL:=https://github.com/tsl0922/ttyd
endef

define Package/ttyd/description
ttyd is a simple command-line tool for sharing terminal over the web with HTTPS/TLS support.
endef

define Package/ttyd/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/ttyd $(1)/usr/bin/
endef

$(eval $(call BuildPackage,ttyd))
