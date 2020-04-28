#(c)Jonathan Warwick-Godfrey 2020

include $(TOPDIR)/rules.mk

PKG_NAME:=darkhttpd
PKG_VERSION:=1.12
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://unix4lyfe.org/darkhttpd/
PKG_HASH:=a50417b622b32b5f421b3132cb94ebeff04f02c5fb87fba2e31147d23de50505
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_MAINTAINER:=Jonathan Warwick-Godfrey <jonathan@petrel.eu.org>
PKG_LICENSE:=ISC

include $(INCLUDE_DIR)/package.mk

define Package/darkhttpd
	SUBMENU:=Web Servers/Proxies
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Simple, fast HTTP 1.1 web server for static content
	URL:=https://unix4lyfe.org/darkhttpd
	USERID:=darkhttpd:www-data
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CC)" \
		CFLAGS="$(TARGET_CFLAGS)" \
		darkhttpd
endef

define Package/darkhttpd/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(PKG_NAME) $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/$(PKG_NAME).init $(1)/etc/init.d/$(PKG_NAME)
	
endef

$(eval $(call BuildPackage,darkhttpd))
