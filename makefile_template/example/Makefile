include make.cfg

MAKE = @ make
export MAKE

CROSS_COMPILE = 
AS		= @ $(CROSS_COMPILE)as
LD		= @ $(CROSS_COMPILE)ld
CC		= @ $(CROSS_COMPILE)gcc
CPP		= @ $(CC) -E
AR		= @ $(CROSS_COMPILE)ar
NM		= @ $(CROSS_COMPILE)nm

STRIP		= @ $(CROSS_COMPILE)strip
OBJCOPY		= @ $(CROSS_COMPILE)objcopy
OBJDUMP		= @ $(CROSS_COMPILE)objdump

export AS LD CC CPP AR NM
export STRIP OBJCOPY OBJDUMP

CFLAGS := -Wall -Werror -O2 -g
CFLAGS += $(PATHS)

LDFLAGS := 

export CFLAGS LDFLAGS

TOPDIR := $(shell pwd)
export TOPDIR

TARGET := example


sub_dirs += $(PROJ_ROOT)/domain
sub_dirs += $(PROJ_ROOT)/app

source_files += 


all : start_recursive_build $(TARGET)
	@ echo target \'$(TARGET)\' has been built!


start_recursive_build:
	$(MAKE) -C ./ -f $(TOPDIR)/make.build


$(TARGET) : start_recursive_build
	$(CC) -o $(TARGET) $(PROJ_BUILD_PATH)/built-in.o $(LDFLAGS)


clean:
	@ rm -f $(shell find -name "*.o")
	@ rm -f $(shell find -name "*.d")
	@ rm -rf $(PROJ_BUILD_PATH)
	@ rm -f $(TARGET)
	