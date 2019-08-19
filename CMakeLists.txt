cmake_minimum_required(VERSION 3.10)

project(tomcrypt VERSION 1.18.2)

#-----------------------------------------------------------------------------
# Include required CMake modules
#-----------------------------------------------------------------------------
include(GNUInstallDirs)
include(CMakePackageConfigHelpers)

#-----------------------------------------------------------------------------
# Options
#-----------------------------------------------------------------------------

# Encauth options
option(ENABLE_ENCAUTH_CCM "Enable ccm" TRUE)
option(ENABLE_ENCAUTH_CHACHAPOLY "Enable chachapoly" TRUE)
option(ENABLE_ENCAUTH_EAX "Enable eax" TRUE)
option(ENABLE_ENCAUTH_GCM "Enable gcm" TRUE)
option(ENABLE_ENCAUTH_OCB "Enable ocb" TRUE)
option(ENABLE_ENCAUTH_OCB3 "Enable ocb3" TRUE)

# Hash options
option(ENABLE_HASH_MD "Enable md" TRUE)
option(ENABLE_HASH_RMD "Enable rmd" TRUE)
option(ENABLE_HASH_SHA1 "Enable sha1" TRUE)
option(ENABLE_HASH_SHA2 "Enable sha2" TRUE)
option(ENABLE_HASH_SHA3 "Enable sha3" TRUE)
option(ENABLE_HASH_TIGER "Enable tiger" TRUE)
option(ENABLE_HASH_BLAKE "Enable blake" TRUE)
option(ENABLE_HASH_CHC "Enable chc" TRUE)
option(ENABLE_HASH_HELPER "Enable helper" TRUE)
option(ENABLE_HASH_WHIRL "Enable whirl" TRUE)

# Mac options
option(ENABLE_MAC_BLAKE2 "Enable blake2" TRUE)
option(ENABLE_MAC_F9 "Enable f9" TRUE)
option(ENABLE_MAC_HMAC "Enable hmac" TRUE)
option(ENABLE_MAC_OMAC "Enable omac" TRUE)
option(ENABLE_MAC_PELICAN "Enable pelican" TRUE)
option(ENABLE_MAC_PMAC "Enable pmac" TRUE)
option(ENABLE_MAC_POLY1305 "Enable poly1305" TRUE)
option(ENABLE_MAC_XCBC "Enable xcbc" TRUE)

# Modes options
option(ENABLE_MODE_CBC "Enable cbc mode" TRUE)
option(ENABLE_MODE_CFB "Enable cfb mode" TRUE)
option(ENABLE_MODE_CTR "Enable ctr mode" TRUE)
option(ENABLE_MODE_ECB "Enable ecb mode" TRUE)
option(ENABLE_MODE_F8 "Enable f8 mode" TRUE)
option(ENABLE_MODE_LRW "Enable lrw mode" TRUE)
option(ENABLE_MODE_OFB "Enable ofb mode" TRUE)
option(ENABLE_MODE_XTS "Enable xts mode" TRUE)

# Misc options
option(ENABLE_MISC_BASE16 "Enable base16" TRUE)
option(ENABLE_MISC_BASE32 "Enable base32" TRUE)
option(ENABLE_MISC_BASE64 "Enable base64" TRUE)
option(ENABLE_MISC_CRYPT "Enable crypt" TRUE)
option(ENABLE_MISC_HKDF "Enable hkdf" TRUE)
option(ENABLE_MISC_PADDING "Enable padding" TRUE)
option(ENABLE_MISC_PKCS5 "Enable pkcs5" TRUE)

# Stream options
option(ENABLE_STREAM_CHACHA "Enable chacha stream" TRUE)
option(ENABLE_STREAM_RABBIT "Enable rabbit stream" TRUE)
option(ENABLE_STREAM_RC4 "Enable rc4 stream" TRUE)
option(ENABLE_STREAM_SALSA20 "Enable salsa20 stream" TRUE)
option(ENABLE_STREAM_SOBER128 "Enable sober128 stream" TRUE)
option(ENABLE_STREAM_SOSEMANUK "Enable sosemanuk stream" TRUE)

# Pk options
option(ENABLE_PK_ASN1_DER "Enable asn1 der" TRUE)
option(ENABLE_PK_ASN1_X509 "Enable asn1 x509" TRUE)
option(ENABLE_PK_DH "Enable dh" TRUE)
option(ENABLE_PK_DSA "Enable dsa" TRUE)
option(ENABLE_PK_ECC "Enable ecc" TRUE)
option(ENABLE_PK_PKCS1 "Enable pkcs1" TRUE)
option(ENABLE_PK_RSA "Enable rsa" TRUE)

#-----------------------------------------------------------------------------
# Definitions
#-----------------------------------------------------------------------------
add_definitions(-DUSE_LTM -DLTM_DESC)

#-----------------------------------------------------------------------------
# Subdirectories
#-----------------------------------------------------------------------------
add_subdirectory(src)

#-----------------------------------------------------------------------------
# Library targets
#-----------------------------------------------------------------------------
add_library(${PROJECT_NAME}-shared SHARED
    $<TARGET_OBJECTS:ciphers_shared_obj>
    $<TARGET_OBJECTS:encauth_shared_obj>
    $<TARGET_OBJECTS:hash_shared_obj>
    $<TARGET_OBJECTS:mac_shared_obj>
    $<TARGET_OBJECTS:math_shared_obj>
    $<TARGET_OBJECTS:misc_shared_obj>
    $<TARGET_OBJECTS:modes_shared_obj>
    $<TARGET_OBJECTS:pk_shared_obj>
    $<TARGET_OBJECTS:stream_shared_obj>
    $<TARGET_OBJECTS:prngs_shared_obj>
)

set_target_properties(${PROJECT_NAME}-shared PROPERTIES OUTPUT_NAME ${PROJECT_NAME})
set_target_properties(${PROJECT_NAME}-shared PROPERTIES SOVERSION ${PROJECT_VERSION})

target_include_directories(${PROJECT_NAME}-shared INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/headers>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME}>
)

add_library(${PROJECT_NAME}-static STATIC
    $<TARGET_OBJECTS:ciphers_static_obj>
    $<TARGET_OBJECTS:encauth_static_obj>
    $<TARGET_OBJECTS:hash_static_obj>
    $<TARGET_OBJECTS:mac_static_obj>
    $<TARGET_OBJECTS:math_static_obj>
    $<TARGET_OBJECTS:misc_static_obj>
    $<TARGET_OBJECTS:modes_static_obj>
    $<TARGET_OBJECTS:pk_static_obj>
    $<TARGET_OBJECTS:stream_static_obj>
    $<TARGET_OBJECTS:prngs_static_obj>
)

set_target_properties(${PROJECT_NAME}-static PROPERTIES OUTPUT_NAME ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}-static INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/headers>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME}>
)

#---------------------------------------------------------------------------------------
# Install/export targets and files
#---------------------------------------------------------------------------------------
set(CONFIG_INSTALL_DIR "${CMAKE_INSTALL_LIBDIR}/cmake/lib${PROJECT_NAME}")
set(PROJECT_VERSION_FILE "${CMAKE_CURRENT_BINARY_DIR}/lib${PROJECT_NAME}-config-version.cmake")
set(PROJECT_CONFIG_FILE "lib${PROJECT_NAME}-config.cmake")
set(TARGETS_EXPORT_NAME "lib${PROJECT_NAME}Targets")

# generate package version file
write_basic_package_version_file(
    ${PROJECT_VERSION_FILE}
    VERSION ${PROJECT_VERSION}
    COMPATIBILITY SameMajorVersion
)

# install targets
install(TARGETS ${PROJECT_NAME}-shared
        COMPONENT "runtime"
        EXPORT ${TARGETS_EXPORT_NAME}
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
#         PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME}
)

install(TARGETS ${PROJECT_NAME}-static
        COMPONENT "development"
        EXPORT ${TARGETS_EXPORT_NAME}
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
#         PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME}
)

# install version file
install(FILES ${PROJECT_VERSION_FILE}
        COMPONENT "development"
        DESTINATION ${CONFIG_INSTALL_DIR}
)

# build directory package config
export(EXPORT ${TARGETS_EXPORT_NAME}
       FILE ${PROJECT_CONFIG_FILE}
       NAMESPACE "LTC::"
)

# installed package config
install(EXPORT ${TARGETS_EXPORT_NAME}
        COMPONENT "development"
        DESTINATION ${CONFIG_INSTALL_DIR}
        FILE ${PROJECT_CONFIG_FILE}
        NAMESPACE "LTC::"
)

# add to CMake registry
export(PACKAGE ${PROJECT_NAME})

#---------------------------------------------------------------------------------------
# Create release packages
#---------------------------------------------------------------------------------------
# package release version
set(PACKAGE_RELEASE_VERSION 1)

# determine distribution and architecture
find_program(LSB_RELEASE lsb_release)

execute_process(COMMAND uname -m OUTPUT_VARIABLE MACHINE_ARCH OUTPUT_STRIP_TRAILING_WHITESPACE)

if(LSB_RELEASE)
    execute_process(COMMAND lsb_release -sr OUTPUT_VARIABLE LINUX_DISTRO_VERSION OUTPUT_STRIP_TRAILING_WHITESPACE)
    execute_process(COMMAND lsb_release -si OUTPUT_VARIABLE LINUX_DISTRO OUTPUT_STRIP_TRAILING_WHITESPACE)

    string(TOLOWER ${LINUX_DISTRO} LINUX_DISTRO)

    if(LINUX_DISTRO STREQUAL "opensuse project")
        set(LINUX_DISTRO "opensuse")
    endif()
endif()


# default CPack generators
set(CPACK_GENERATOR TGZ STGZ)

# extra CPack generators
if(LINUX_DISTRO STREQUAL "debian" OR LINUX_DISTRO STREQUAL "ubuntu" OR LINUX_DISTRO STREQUAL "linuxmint")
    list(APPEND CPACK_GENERATOR DEB)
elseif(LINUX_DISTRO STREQUAL "fedora" OR LINUX_DISTRO STREQUAL "opensuse" OR LINUX_DISTRO STREQUAL "centos")
    list(APPEND CPACK_GENERATOR RPM)
endif()

# general CPack config
set(CPACK_PACKAGE_DIRECTORY ${CMAKE_BINARY_DIR}/packages)
message(STATUS "CPack: packages will be generated under ${CPACK_PACKAGE_DIRECTORY}")
set(CPACK_PACKAGE_NAME "lib${PROJECT_NAME}")
set(CPACK_PACKAGE_VERSION ${PROJECT_VERSION})
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "LibTomCrypt")
set(CPACK_PACKAGE_VENDOR "LibTomCrypt")
set(CPACK_PACKAGE_CONTACT "foo@bar.com")
set(CPACK_RESOURCE_FILE_LICENSE "${PROJECT_SOURCE_DIR}/LICENSE")
set(CPACK_PACKAGE_FILE_NAME ${CPACK_PACKAGE_NAME}-${CPACK_PACKAGE_VERSION}-${PACKAGE_RELEASE_VERSION}-Linux-${MACHINE_ARCH})
set(CPACK_STRIP_FILES ON)

# deb specific CPack config
set(CPACK_DEBIAN_PACKAGE_RELEASE ${PACKAGE_RELEASE_VERSION})
set(CPACK_DEBIAN_FILE_NAME DEB-DEFAULT)
set(CPACK_DEBIAN_PACKAGE_SHLIBDEPS ON)
set(CPACK_DEBIAN_PACKAGE_HOMEPAGE "https://github.com/libtom/libtomcrypt")
set(CPACK_DEBIAN_PACKAGE_SECTION "devel")

# rpm specific CPack config
set(CPACK_RPM_PACKAGE_URL "https://github.com/libtom/libtomcrypt")
set(CPACK_RPM_PACKAGE_RELEASE ${PACKAGE_RELEASE_VERSION})
set(CPACK_RPM_PACKAGE_ARCHITECTURE ${MACHINE_ARCH})
set(CPACK_RPM_PACKAGE_NAME "${PROJECT_NAME}-${PROJECT_VERSION}")
set(CPACK_RPM_FILE_NAME "${PROJECT_NAME}_${PROJECT_VERSION}-${CPACK_RPM_PACKAGE_RELEASE}_${LINUX_DISTRO}-${LINUX_DISTRO_VERSION}_${CPACK_RPM_PACKAGE_ARCHITECTURE}.rpm")
set(CPACK_RPM_PACKAGE_LICENSE "WTFPL")

include(CPack)
