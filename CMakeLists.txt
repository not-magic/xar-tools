cmake_minimum_required(VERSION 3.0.0 FATAL_ERROR)
project(pbzx_cmake)

find_package(LibXml2)
find_package(ZLIB)
find_package(LibLZMA)
find_package(OpenSSL)

set(XAR_VERSION "1.6.1")
set(XAR_NUMERIC_VERSION 0x01060180)
set(C99_FIXED_WIDTH_TYPE_HEADER "#include <stdint.h>")

configure_file(xar/xar/include/xar.h.in xar.h)

add_library(libxar STATIC
	xar/xar/lib/archive.c
	xar/xar/lib/arcmod.c
	xar/xar/lib/b64.c
	xar/xar/lib/bzxar.c
	xar/xar/lib/darwinattr.c
	xar/xar/lib/data.c
	xar/xar/lib/ea.c
	xar/xar/lib/err.c
	xar/xar/lib/ext2.c
	xar/xar/lib/fbsdattr.c
	xar/xar/lib/filetree.c
	xar/xar/lib/hash.c
	xar/xar/lib/io.c
	xar/xar/lib/linuxattr.c
	xar/xar/lib/lzmaxar.c
	xar/xar/lib/macho.c
	xar/xar/lib/script.c
	xar/xar/lib/signature.c
	xar/xar/lib/stat.c
	xar/xar/lib/subdoc.c
	xar/xar/lib/util.c
	xar/xar/lib/zxar.c
)
target_link_libraries(libxar PUBLIC LibXml2::LibXml2 ZLIB::ZLIB LibLZMA::LibLZMA OpenSSL::Crypto)
target_include_directories(libxar PUBLIC xar/xar/include xar_config ${CMAKE_CURRENT_BINARY_DIR})

add_executable(pbzx
	pbzx/pbzx.c
)
add_executable(xar
	xar/xar/src/xar.c
)

#target_include_directories(pbzx PUBLIC xar/include)
target_link_libraries(pbzx libxar)

#target_include_directories(xar PUBLIC xar/include)
target_link_libraries(xar libxar)
