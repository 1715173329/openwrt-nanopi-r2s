include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_VERSION:=2020.04
PKG_RELEASE:=1
PKG_HASH:=fe732aaf037d9cc3c0909bad8362af366ae964bbdac6913a34081ff4ad565372

include $(INCLUDE_DIR)/u-boot.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk

define U-Boot/Default
  BUILD_TARGET:=mediatek
  UBOOT_IMAGE:=u-boot-mtk.bin
  DEFAULT:=y
endef

define U-Boot/mt7629
  NAME:=MT7629
  BUILD_SUBTARGET:=mt7629
  UBOOT_CONFIG:=mt7629_rfb
endef

define U-Boot/mt7622
  NAME:=MT7622
  BUILD_SUBTARGET:=mt7622
  UBOOT_CONFIG:=mt7622_rfb
endef

define U-Boot/mt7623n_bpir2
  NAME:=Banana Pi R2 (mt7623)
  BUILD_SUBTARGET:=mt7623
  UBOOT_IMAGE:=u-boot.bin
  UBOOT_CONFIG:=mt7623n_bpir2
endef

UBOOT_TARGETS := mt7629 mt7622 mt7623n_bpir2

UBOOT_MAKE_FLAGS += $(UBOOT_IMAGE)

Build/Exports:=$(Host/Exports)

define Build/InstallDev
	$(INSTALL_DIR) $(STAGING_DIR_IMAGE)
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(UBOOT_IMAGE) $(STAGING_DIR_IMAGE)/$(BUILD_VARIANT)-$(UBOOT_IMAGE)
endef

$(eval $(call BuildPackage/U-Boot))
