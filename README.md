libiconv-1.14-android
=====================

libiconv 1.14 for android

修改的地方：
1 LOCAL_PATH := $(call my-dir)
  2 
  3 #libiconv.so
  4 LOCAL_MODULE := iconv
  5 LOCAL_MODULE_FILENAME := libiconv     # add here ,name must start with lib
  6 LOCAL_CFLAGS := \
  7   -Wno-multichar \
  8   -D_ANDROID \                   # modify here
  9   -DLIBDIR="c" \
 10   -DBUILDING_LIBICONV \
 11   -DIN_LIBRARY
 12 
 13 LOCAL_C_INCLUDES += \
 14   $(LOCAL_PATH)/libiconv-1.14/include \
 15   $(LOCAL_PATH)/libiconv-1.14/libcharset \
 16   $(LOCAL_PATH)/libiconv-1.14/lib \
 17   $(LOCAL_PATH)/libiconv-1.14/libcharset/include \
 18   $(LOCAL_PATH)/libiconv-1.14/srclib
 19 
 20 LOCAL_SRC_FILES := \
 21   libiconv-1.14/lib/iconv.c \
 22   libiconv-1.14/lib/relocatable.c \
 23   libiconv-1.14/libcharset/lib/localcharset.c
 24 
 25 LOCAL_EXPORT_C_INCLUDES       := $(LOCAL_PATH)/libiconv-1.14/include
 26 include $(BUILD_SHARED_LIBRARY)
 27 #include $(BUILD_STATIC_LIBRARY)
