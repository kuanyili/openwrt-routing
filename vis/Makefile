#
# Copyright (C) 2008-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=vis
PKG_RELEASE:=9

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2013-04-07
PKG_SOURCE_VERSION:=7710cce42e8d63ea114056a4a140835d4a452933
PKG_SOURCE_URL:=https://git.open-mesh.org/vis.git
PKG_MIRROR_HASH:=2544df816f9294e192cd6bb3592695416796fc6b254d182f1f124e686833f50d

PKG_MAINTAINER:=Corinna "Elektra" Aichele <onelektra@gmx.net>
PKG_LICENSE:=GPL-2.0-only

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/vis
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Routing and Redirection
  DEPENDS:=+libpthread
  TITLE:=visualization server for B.A.T.M.A.N. layer 3
  URL:=https://www.open-mesh.org/
endef

define Package/vis/description
visualization server for B.A.T.M.A.N. layer 3
endef

MAKE_FLAGS += \
	EXTRA_CFLAGS='-DDEBUG_MALLOC -DMEMORY_USAGE -DPROFILE_DATA -DREVISION_VERSION=\"\ rv$(PKG_REV)\" -D_GNU_SOURCE' \
	REVISION="$(PKG_REV)" \
	CC="$(TARGET_CC)" \
	vis

define Package/vis/install
	$(INSTALL_DIR) $(1)/usr/sbin $(1)/etc/config $(1)/etc/init.d
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/vis $(1)/usr/sbin/
	$(INSTALL_BIN) ./files/etc/init.d/vis $(1)/etc/init.d
	$(INSTALL_DATA) ./files/etc/config/vis $(1)/etc/config
endef

define Package/vis/conffiles
/etc/config/vis
endef

$(eval $(call BuildPackage,vis))
