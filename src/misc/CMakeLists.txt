# Misc options
option(ENABLE_MISC_BASE16 "Enable base16" TRUE)
option(ENABLE_MISC_BASE32 "Enable base32" TRUE)
option(ENABLE_MISC_BASE64 "Enable base64" TRUE)
option(ENABLE_MISC_CRYPT "Enable crypt" TRUE)
option(ENABLE_MISC_HKDF "Enable hkdf" TRUE)
option(ENABLE_MISC_PADDING "Enable padding" TRUE)
option(ENABLE_MISC_PKCS5 "Enable pkcs5" TRUE)

set(MISC_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/copy_or_zeromem.c
    ${CMAKE_CURRENT_SOURCE_DIR}/error_to_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/burn_stack.c
#     ${CMAKE_CURRENT_SOURCE_DIR}/pk_get_oid.c
    ${CMAKE_CURRENT_SOURCE_DIR}/crc32.c
    ${CMAKE_CURRENT_SOURCE_DIR}/compare_testvector.c
    ${CMAKE_CURRENT_SOURCE_DIR}/adler32.c
    ${CMAKE_CURRENT_SOURCE_DIR}/mem_neq.c
    ${CMAKE_CURRENT_SOURCE_DIR}/zeromem.c
)

#-----------------------------------------------------------------------------
# Add subdirectories sources depending on enabled options
#-----------------------------------------------------------------------------
if(ENABLE_MISC_BASE16)
    add_subdirectory(base16)
    list(APPEND MISC_SOURCES ${MISC_BASE16_SOURCES})
endif()

if(ENABLE_MISC_BASE32)
    add_subdirectory(base32)
    list(APPEND MISC_SOURCES ${MISC_BASE32_SOURCES})
endif()

if(ENABLE_MISC_BASE64)
    add_subdirectory(base64)
    list(APPEND MISC_SOURCES ${MISC_BASE64_SOURCES})
endif()

if(ENABLE_MISC_CRYPT)
    add_subdirectory(crypt)
    list(APPEND MISC_SOURCES ${MISC_CRYPT_SOURCES})
endif()

if(ENABLE_MISC_HKDF)
    add_subdirectory(hkdf)
    list(APPEND MISC_SOURCES ${MISC_HKDF_SOURCES})
endif()

if(ENABLE_MISC_PADDING)
    add_subdirectory(padding)
    list(APPEND MISC_SOURCES ${MISC_PADDING_SOURCES})
endif()

if(ENABLE_MISC_PKCS5)
    add_subdirectory(pkcs5)
    list(APPEND MISC_SOURCES ${MISC_PKCS5_SOURCES})
endif()

#-----------------------------------------------------------------------------
# MISC
#-----------------------------------------------------------------------------
target_sources(${PROJECT_NAME}-shared PRIVATE ${MISC_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MISC_SOURCES})
