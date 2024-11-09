# SPDX-License-Identifier: GPL-2.0

# Define KERNEL_SRC to locate the kernel source for DKMS builds
KERNEL_SRC ?= /lib/modules/$(shell uname -r)/build
obj-m += rknpu.o

# Include directory for headers
ccflags-y += -I$(srctree)/$(src)/include
ccflags-y += -I$(src)/include
ccflags-y += -Werror

# Object files for the rknpu module
rknpu-y += rknpu_drv.o
rknpu-y += rknpu_reset.o
rknpu-y += rknpu_job.o
rknpu-y += rknpu_debugger.o
rknpu-y += rknpu_iommu.o
rknpu-$(CONFIG_PM_DEVFREQ) += rknpu_devfreq.o
rknpu-$(CONFIG_ROCKCHIP_RKNPU_SRAM) += rknpu_mm.o
rknpu-$(CONFIG_ROCKCHIP_RKNPU_FENCE) += rknpu_fence.o
rknpu-$(CONFIG_ROCKCHIP_RKNPU_DRM_GEM) += rknpu_gem.o
rknpu-$(CONFIG_ROCKCHIP_RKNPU_DMA_HEAP) += rknpu_mem.o

# Build and clean targets for DKMS compatibility
all:
	$(MAKE) -C $(KERNEL_SRC) M=$(PWD) modules

clean:
	$(MAKE) -C $(KERNEL_SRC) M=$(PWD) clean

