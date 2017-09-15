#
# Copyright (C) 2015-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lxml
PKG_VERSION:=3.8.0
PKG_RELEASE:=1
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/20/b3/9f245de14b7696e2d2a386c0b09032a2ff6625270761d6543827e667d8de
PKG_MD5SUM:=e54e2fae44d684d6b9c636fe189e93ff

PKG_BUILD_DEPENDS:=python python-setuptools
HOST_BUILD_DEPENDS:=python/host python-setuptools/host  libxml2/host libxslt/host

PKG_LICENSE:=BSD
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:= Maintainers <maintainers@entware.net>

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)
$(call include_mk, python-host.mk)

define Package/python-lxml
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python-lxml
	URL:=http://http://lxml.de/index.html
	DEPENDS:=+python +libxml2 +libexslt +librt
endef

define Package/python-lxml/description
 The lxml XML toolkit is a Pythonic binding for the C libraries libxml2 and libxslt.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix="/opt" --root="$(PKG_INSTALL_DIR)")
endef

define Host/Compile
	$(call Build/Compile/HostPyMod,,install --prefix="" --root="$(HOST_BUILD_PREFIX)")
endef

define Host/Install
endef

$(eval $(call HostBuild))

$(eval $(call PyPackage,python-lxml))
$(eval $(call BuildPackage,python-lxml))
