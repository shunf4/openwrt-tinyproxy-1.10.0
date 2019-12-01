#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=tinyproxy-new
PKG_VERSION:=1.10.0
PKG_RELEASE:=3

PKG_SOURCE:=tinyproxy-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://github.com/tinyproxy/tinyproxy/releases/download/1.10.0/
PKG_HASH:=a23a8f647f622f01e51b93fa882ea5a15c20e026d45c3aafa81ec579e464daf7
PKG_MAINTAINER:=Jo-Philipp Wich <jo@mein.io>

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/tinyproxy-new
  SUBMENU:=Web Servers/Proxies
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Tinyproxy is a lightweight HTTP and HTTPS proxy
  URL:=http://tinyproxy.sourceforge.net/
endef

define Package/tinyproxy/conffiles
/etc/config/tinyproxy
endef

CONFIGURE_ARGS+= \
	--enable-filter \
	--enable-transparent \
	--disable-regexcheck \

define Package/tinyproxy/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/tinyproxy $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/usr/share/tinyproxy
	$(CP) $(PKG_INSTALL_DIR)/usr/share/tinyproxy/*.html $(1)/usr/share/tinyproxy/
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/tinyproxy.config $(1)/etc/config/tinyproxy
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/tinyproxy.init $(1)/etc/init.d/tinyproxy
endef

$(eval $(call BuildPackage,tinyproxy-new))