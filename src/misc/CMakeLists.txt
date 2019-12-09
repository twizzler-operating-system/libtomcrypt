#-----------------------------------------------------------------------------
# Misc options
#-----------------------------------------------------------------------------
set(MISC_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/copy_or_zeromem.c
    ${CMAKE_CURRENT_SOURCE_DIR}/error_to_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/burn_stack.c
    ${CMAKE_CURRENT_SOURCE_DIR}/crc32.c
    ${CMAKE_CURRENT_SOURCE_DIR}/compare_testvector.c
    ${CMAKE_CURRENT_SOURCE_DIR}/adler32.c
    ${CMAKE_CURRENT_SOURCE_DIR}/mem_neq.c
    ${CMAKE_CURRENT_SOURCE_DIR}/zeromem.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MISC_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MISC_SOURCES})

#-----------------------------------------------------------------------------
# Add subdirectories
#-----------------------------------------------------------------------------
add_subdirectory(base16)
add_subdirectory(base32)
add_subdirectory(base64)
add_subdirectory(crypt)
add_subdirectory(hkdf)
add_subdirectory(padding)
add_subdirectory(pkcs12)
add_subdirectory(pkcs5)
add_subdirectory(ssh)
add_subdirectory(pbes)
