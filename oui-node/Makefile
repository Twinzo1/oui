
  SECTION:=oui
  CATEGORY:=OUI
  TITLE:=node for OUI 
  URL:=http://nodejs.org/
  DEPENDS:=+libpthread +librt +libstdcpp +libopenssl +libuv
endef

define Package/oui-node/description
	oui node componet
endef

CONFIGURE_ARGS= \
	--dest-cpu=$(CONFIG_ARCH) \
	--dest-os=linux \
	--without-snapshot \
	--shared-zlib \
	--shared-openssl \
	--prefix=/usr

HOST_CONFIGURE_VARS:=
HOST_CONFIGURE_ARGS:= \
	--dest-os=linux \
	--without-snapshot \
	--prefix=$(STAGING_DIR_HOST)/

HOST_CONFIGURE_CMD:=python ./configure

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
endef

define Package/oui-node/install
	mkdir -p $(1)/usr/bin $(1)/usr/lib/node_modules/npm/{bin,lib,node_modules}
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/{node,npm} $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/node_modules/npm/{package.json,LICENSE,cli.js} $(1)/usr/lib/node_modules/npm
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/node_modules/npm/bin/npm-cli.js $(1)/usr/lib/node_modules/npm/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/node_modules/npm/lib/* $(1)/usr/lib/node_modules/npm/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/node_modules/npm/node_modules/* $(1)/usr/lib/node_modules/npm/node_modules/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,oui-node))
