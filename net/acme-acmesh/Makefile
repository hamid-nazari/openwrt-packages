#
# Copyright (C) 2016 Toke Høiland-Jørgensen
#
# This is free software, licensed under the GNU General Public License v3 or
# later.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=acme-acmesh
PKG_VERSION:=3.0.1
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/acmesh-official/acme.sh/tar.gz/$(PKG_VERSION)?
PKG_HASH:=6212cc0c2bca99a7dd6cbb4236b4c7dd5d1113dab0841e66dae4d307d902a8e6
PKG_BUILD_DIR:=$(BUILD_DIR)/acme.sh-$(PKG_VERSION)

PKG_MAINTAINER:=Toke Høiland-Jørgensen <toke@toke.dk>
PKG_LICENSE:=GPL-3.0-only
PKG_LICENSE_FILES:=LICENSE.md

include $(INCLUDE_DIR)/package.mk

define Package/acme-acmesh
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+acme-common +wget-ssl +ca-bundle +openssl-util +socat
  TITLE:=ACME client acme.sh wrapper script
  URL:=https://acme.sh
  PKGARCH:=all
  PROVIDES:=acme-client
endef

define Package/acme-acmesh/description
A client for issuing ACME (e.g, Letsencrypt) certificates.
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/acme-acmesh/install
	$(INSTALL_DIR) $(1)/usr/lib/acme/client
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/acme.sh $(1)/usr/lib/acme/client
	$(INSTALL_BIN) ./files/hook.sh $(1)/usr/lib/acme/hook
endef

define Package/acme-acmesh-dnsapi
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+acme
  TITLE:=DNS API integration for ACME (Letsencrypt) client
  PKGARCH:=all
endef

define Package/acme-acmesh-dnsapi/description
 This package provides DNS API integration for ACME (Letsencrypt) client.
endef

define Package/acme-acmesh-dnsapi/install
	$(INSTALL_DIR) $(1)/usr/lib/acme/client/dnsapi
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/dnsapi/*.sh $(1)/usr/lib/acme/client/dnsapi
endef

$(eval $(call BuildPackage,acme-acmesh))
$(eval $(call BuildPackage,acme-acmesh-dnsapi))
