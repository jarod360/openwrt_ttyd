#
# Copyright (C) 2025 Jarod
# Modified OpenWrt Makefile for libwebsockets with full SSL/TLS support
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libwebsockets-full
PKG_VERSION:=4.3.3
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/warmcat/libwebsockets.git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_MIRROR_HASH:=skip

PKG_MAINTAINER:=Jarod <jarod@example.com>
PKG_LICENSE:=LGPL-2.1
PKG_LICENSE_FILES:=LICENSE
PKG_CPE_ID:=cpe:/a:libwebsockets:libwebsockets

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libwebsockets-full
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Full-featured libwebsockets (with SSL/TLS, HTTP/2)
  URL:=https://libwebsockets.org
  DEPENDS:=+libopenssl +libuv +zlib
endef

define Package/libwebsockets-full/description
libwebsockets is a lightweight pure C library providing
fully featured WebSockets, HTTP/2, and TLS (OpenSSL) support.

This "full" version enables SSL/TLS, HTTP/2, IPv6,
permessage-deflate, and websocket extensions.
endef

CMAKE_OPTIONS += \
	-DLWS_WITH_SSL=ON \
	-DLWS_WITH_HTTP2=ON \
	-DLWS_WITH_HTTP_STREAM_COMPRESSION=ON \
	-DLWS_WITH_ZLIB=ON \
	-DLWS_WITHOUT_EXTENSIONS=OFF \
	-DLWS_WITH_IPV6=ON \
	-DLWS_WITH_SOCKS5=ON \
	-DLWS_WITH_PLUGINS=ON \
	-DLWS_WITH_STATIC=OFF \
	-DLWS_OPENSSL_INCLUDE_DIRS=$(STAGING_DIR)/usr/include \
	-DLWS_OPENSSL_LIBRARIES=$(STAGING_DIR)/usr/lib \
	-DLWS_WITH_MBEDTLS=OFF \
	-DLWS_WITH_SHARED=ON \
	-DCMAKE_BUILD_TYPE=Release

define Package/libwebsockets-full/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/lib/libwebsockets.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libwebsockets-full))
