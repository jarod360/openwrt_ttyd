# Copyright (C) 2016 Openwrt.org
#
# This is free software, licensed under the Apache License, Version 2.0 .
#

include $(TOPDIR)/rules.mk

LUCI_TITLE:=LuCI support for ttyd
LUCI_DEPENDS:=+ttyd
LUCI_PKGARCH:=all

# 关键修改：禁用独立语言包生成
LUCI_BUILD_NAMES:=

PKG_NAME:=luci-app-ttyd
PKG_VERSION:=2.2
PKG_RELEASE:=3  # 增加版本号

include $(TOPDIR)/feeds/luci/luci.mk

# 强制包含中文翻译到主包
define Package/$(PKG_NAME)/install
	$(CP) $(PKG_BUILD_DIR)/usr/lib/lua/luci/i18n/* $(1)/usr/lib/lua/luci/i18n/ 2>/dev/null || true
endef

# call BuildPackage - OpenWrt buildroot signature
