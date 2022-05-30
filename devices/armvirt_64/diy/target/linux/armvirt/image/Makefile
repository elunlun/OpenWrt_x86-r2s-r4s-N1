# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2012-2019 OpenWrt.org
# Copyright (C) 2016-2017 LEDE project

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

define Build/Compile
	$(CP) $(LINUX_DIR)/COPYING $(KDIR)/COPYING.linux
endef

### Devices ###
define Device/Default
  KERNEL := kernel-bin
endef

define Device/n1
  DEVICE_VENDOR := Phicomm
  DEVICE_MODEL := N1
  SOC := s905d
  DEVICE_PACKAGES :=
endef
TARGET_DEVICES += n1



define Image/Build
	export IMG_PREFIX="$(IMG_PREFIX)$(if $(PROFILE_SANITIZED),-$(PROFILE_SANITIZED))"; \
	export BIN_DIR=$(BIN_DIR); \
	export PARTSIZE=$(CONFIG_TARGET_ROOTFS_PARTSIZE); \
	cd $(TOPDIR)/../openwrt_packit; \
	./mk_s905d_n1.sh; \
	gzip -f9n $(BIN_DIR)/$(IMG_PREFIX)$(if $(PROFILE_SANITIZED),-n1).img || true; \
	rm -f $(BIN_DIR)/*.tar.gz
endef

$(eval $(call BuildImage))

# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2020 Tobias Maedel
