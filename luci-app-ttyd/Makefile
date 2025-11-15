include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-ttyd
PKG_VERSION:=2.0
PKG_RELEASE:=1

LUCI_TITLE:=LuCI Support for ttyd
LUCI_DEPENDS:=+ttyd
LUCI_PKGARCH:=all

# 关键补丁：禁止 LuCI 2024.x 的 PKG_VERSION 模板替换，否则会 sed 崩溃
LUCI_NO_COMMIT:=1

include $(TOPDIR)/feeds/luci/luci.mk

# 兼容 LuCI 新版本，不使用老式 PKG_VERSION 替换机制
define Package/$(PKG_NAME)/install
	$(call Package/luci/install,$(1))
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
