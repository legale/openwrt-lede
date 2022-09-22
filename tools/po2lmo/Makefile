include $(TOPDIR)/rules.mk

PKG_NAME:=po2lmo
PKG_VERSION:=1.2.1
PKG_RELEASE:=1


HOST_BUILD_PARALLEL:=1

HOSTCC := $(HOSTCC_NOCACHE)
HOSTCXX := $(HOSTCXX_NOCACHE)

include $(INCLUDE_DIR)/host-build.mk

define Host/Prepare
	mkdir -p $(HOST_BUILD_DIR)
	$(CP) ./src/* $(HOST_BUILD_DIR)/
	find $(HOST_BUILD_DIR) -name .svn | $(XARGS) rm -rf
endef

define Host/Compile
	$(MAKE) $(HOST_JOBS) -C $(HOST_BUILD_DIR)/po2lmo SHELL="$(BASH)"
endef

define Host/Install
	$(INSTALL_BIN) $(HOST_BUILD_DIR)/po2lmo/src/po2lmo $(STAGING_DIR_HOST)/bin/
endef

define Host/Clean
	rm -f $(STAGING_DIR_HOST)/bin/po2lmo
endef


$(eval $(call HostBuild))
