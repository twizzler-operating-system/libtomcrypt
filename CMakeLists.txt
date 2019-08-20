cmake_minimum_required(VERSION 3.10)

project(tomcrypt VERSION 1.18.2)

#-----------------------------------------------------------------------------
# Include required CMake modules
#-----------------------------------------------------------------------------
include(GNUInstallDirs)
include(CMakePackageConfigHelpers)
include(FindPkgConfig)

#-----------------------------------------------------------------------------
# Options
#-----------------------------------------------------------------------------
option(USE_LTM "Build with libtommath" TRUE)

#-----------------------------------------------------------------------------
# Library targets
#-----------------------------------------------------------------------------
add_library(${PROJECT_NAME}-shared SHARED)
add_library(${PROJECT_NAME}-static STATIC)

#-----------------------------------------------------------------------------
# Definitions
#-----------------------------------------------------------------------------

if(USE_LTM)
    pkg_check_modules(LTM REQUIRED IMPORTED_TARGET libtommath>=1.1.0)

    target_compile_definitions(${PROJECT_NAME}-shared PUBLIC USE_LTM LTM_DESC)
    target_compile_definitions(${PROJECT_NAME}-static PUBLIC USE_LTM LTM_DESC)
endif()

#-----------------------------------------------------------------------------
# Add subdirectories
#-----------------------------------------------------------------------------
add_subdirectory(src)

#-----------------------------------------------------------------------------
# Public headers
#-----------------------------------------------------------------------------
get_property(${PROJECT_NAME}-public-headers GLOBAL PROPERTY PUBLIC_HEADERS)

#-----------------------------------------------------------------------------
# Library target properties
#-----------------------------------------------------------------------------

# shared
set_target_properties(${PROJECT_NAME}-shared PROPERTIES OUTPUT_NAME ${PROJECT_NAME})
set_target_properties(${PROJECT_NAME}-shared PROPERTIES SOVERSION ${PROJECT_VERSION})
set_target_properties(${PROJECT_NAME}-shared PROPERTIES PUBLIC_HEADER "${${PROJECT_NAME}-public-headers}")

target_include_directories(${PROJECT_NAME}-shared PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/headers>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/lib${PROJECT_NAME}>
)

# static
set_target_properties(${PROJECT_NAME}-static PROPERTIES OUTPUT_NAME ${PROJECT_NAME})
set_target_properties(${PROJECT_NAME}-static PROPERTIES PUBLIC_HEADER "${${PROJECT_NAME}-public-headers}")

target_include_directories(${PROJECT_NAME}-static PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/headers>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/lib${PROJECT_NAME}>
)

# libtommath dependent
if(USE_LTM)
    target_link_libraries(${PROJECT_NAME}-shared INTERFACE PkgConfig::LTM)
    target_link_libraries(${PROJECT_NAME}-static INTERFACE PkgConfig::LTM)
endif()

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
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/lib${PROJECT_NAME}
)

install(TARGETS ${PROJECT_NAME}-static
        COMPONENT "development"
        EXPORT ${TARGETS_EXPORT_NAME}
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/lib${PROJECT_NAME}
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
