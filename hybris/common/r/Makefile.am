bionic = $(top_srcdir)/common/r/bionic
bionic_libc = $(bionic)/libc

modlibexecdir = $(libdir)/libhybris/linker
modlibexec_LTLIBRARIES = r.la

ARCH_FLAGS =

AM_CFLAGS = \
	-std=gnu99

AM_CPPFLAGS = \
	-fno-stack-protector \
	-Wstrict-overflow=5

AM_CXXFLAGS = \
	-std=gnu++11 \
	-Wold-style-cast

r_la_SOURCES = \
	hybris_compat.cpp \
	dlfcn.cpp \
	linker_block_allocator.cpp \
	linker.cpp \
	linker_cfi.cpp \
	linker_config.cpp \
	linker_dlwarning.cpp \
	linker_gdb_support.cpp \
	linker_globals.cpp \
	linker_logger.cpp \
	linker_main.cpp \
	linker_mapped_file_fragment.cpp \
	linker_memory.cpp \
	linker_namespaces.cpp \
	linker_phdr.cpp \
	linker_relocate.cpp \
	linker_sdk_versions.cpp \
	linker_soinfo.cpp \
	linker_tls.cpp \
	linker_translate_path.cpp \
	linker_utils.cpp \
	linker_debug.cpp \
	linker_debuggerd_android.cpp \
	linker_debuggerd_stub.cpp \
	rt.cpp \
        arch/arm_neon/linker_gnu_hash_neon.cpp \
	bionic/libc/bionic/bionic_call_ifunc_resolver.cpp \
        arch/arm64/tlsdesc_resolver.S \
	../strlcpy.c \
	../strlcat.c
r_la_CPPFLAGS = \
	$(AM_CPPFLAGS) \
	-I$(top_srcdir)/include \
	-I$(top_srcdir)/common \
	-I$(bionic_libc)/ \
	-I$(bionic_libc)/include \
	-DDEFAULT_HYBRIS_LD_LIBRARY_PATH="\"@DEFAULT_HYBRIS_LD_LIBRARY_PATH@\"" \
	-D_USING_LIBCXX \
	$(ARCH_FLAGS) \
	$(ANDROID_HEADERS_CFLAGS)
r_la_LDFLAGS = \
	-lsupc++ \
	-module \
	-avoid-version

if WANT_DEBUG
r_la_CPPFLAGS += \
	-DTRACE_DEBUG=1
else
r_la_CPPFLAGS += \
	-DTRACE_DEBUG=1
endif

if WANT_ARM_TRACING
r_la_CPPFLAGS += \
	-DWANT_ARM_TRACING
endif

