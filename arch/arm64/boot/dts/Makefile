# SPDX-License-Identifier: GPL-2.0
subdir-y += actions
subdir-y += allwinner
subdir-y += altera
subdir-y += amazon
subdir-y += amd
subdir-y += amlogic
subdir-y += apm
subdir-y += apple
subdir-y += arm
subdir-y += bitmain
subdir-y += broadcom
subdir-y += cavium
subdir-y += exynos
subdir-y += freescale
subdir-y += hisilicon
subdir-y += intel
subdir-y += lg
subdir-y += marvell
subdir-y += mediatek
subdir-y += microchip
subdir-y += nvidia
subdir-y += qcom
subdir-y += realtek
subdir-y += renesas
subdir-y += rockchip
subdir-y += socionext
subdir-y += sprd
subdir-y += synaptics
subdir-y += tesla
subdir-y += ti
subdir-y += toshiba
subdir-y += xilinx


dtstree		:= $(srctree)/$(src)

vendor := $(dtstree)/vendor
ifneq "$(wildcard $(vendor)/Makefile)" ""
        subdir-y += vendor
endif

dtb-$(CONFIG_OF_ALL_DTBS) := $(patsubst $(dtstree)/%.dts,%.dtb, $(foreach d,$(subdir), $(wildcard $(dtstree)/$(d)/*.dts)))

always		:= $(dtb-y)

targets += dtbs

DTB_NAMES := $(subst $\",,$(CONFIG_BUILD_ARM64_APPENDED_DTB_IMAGE_NAMES))
ifneq ($(DTB_NAMES),)
DTB_LIST := $(addsuffix .dtb,$(DTB_NAMES))
else
DTB_LIST := $(dtb-y)
endif
targets += $(DTB_LIST)

dtbs: $(addprefix $(obj)/, $(DTB_LIST))

clean-files := dts/*.dtb *.dtb
