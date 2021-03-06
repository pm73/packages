#
# Copyright (C) 2007-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libsndfile
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/erikd/libsndfile.git
PKG_SOURCE_DATE:=2018-12-24
PKG_SOURCE_VERSION:=8ddc442d539ca775d80cdbc7af17a718634a743f
PKG_MIRROR_HASH:=d7be85919067f51c83b74b67ea9e7043710fe009d704aa414ef57c6f48974ae1

PKG_LICENSE:=LGPLv2.1
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libsndfile
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Library for reading/writing audio files
  URL:=http://www.mega-nerd.com/libsndfile/
  MAINTAINER:=Peter Wagner <tripolar@gmx.at>
endef

define Package/libsndfile/description
 libsndfile is a library of C routines for reading and writing files
 containing sampled audio data.
endef

CMAKE_OPTIONS += \
	-DBUILD_SHARED_LIBS:BOOL=ON \
	-DENABLE_EXTERNAL_LIBS:BOOL=FALSE \
	-DBUILD_REGTEST:BOOL=FALSE

TARGET_CFLAGS += $(FPIC)

define Build/InstallDev
	$(INSTALL_DIR) $(1)
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

define Package/libsndfile/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libsndfile.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libsndfile))
