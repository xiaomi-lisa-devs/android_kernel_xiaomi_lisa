ifneq ($(KERNELRELEASE),)
		obj-$(CONFIG_TOUCHSCREEN_GOODIX_BRL_K9)            += goodix_core.o
		goodix_core-y := goodix_ts_core.o goodix_brl_hw.o goodix_cfg_bin.o goodix_ts_utils.o \
				goodix_brl_fwupdate.o goodix_brl_spi.o goodix_ts_test.o
		obj-$(CONFIG_TOUCHSCREEN_GOODIX_TS_TOOLS_K9)       += goodix_ts_tools.o
		obj-$(CONFIG_TOUCHSCREEN_GOODIX_TS_GESTURE_K9)     += goodix_ts_gesture.o

else
    KDIR = $(OUT)/obj/KERNEL_OBJ
    CROSS_COMPILE = $(ANDROID_TOOLCHAIN)/aarch64-linux-android-
    CLANG = $(ANDROID_BUILD_TOP)/prebuilts/clang/host/linux-x86/clang-r370808
    REAL_CC = $(CLANG)/bin/clang
    AR = $(CLANG)/bin/llvm-ar
    LLVM_NM = $(CLANG)/bin/llvm-nm
    LD = $(CLANG)/bin/ld.lld

.PHONY: clean

default:
	$(MAKE) ARCH=arm64 CROSS_COMPILE=$(CROSS_COMPILE) REAL_CC=$(REAL_CC) CLANG_TRIPLE=aarch64-linux-gnu- AR=$(AR) LLVM_NM=$(LLVM_NM) LD=$(LD) -C $(KDIR) M=$(PWD) modules
clean:
	@rm -rf *.o* *.order *.symvers *.mod* .*.o.cmd .*.mod.o.cmd .*.ko.cmd .tmp_versions *.ko
	@find -name *.o | xargs rm -f
endif
