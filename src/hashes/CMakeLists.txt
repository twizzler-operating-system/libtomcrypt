set(HASH_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/md4.c
    ${CMAKE_CURRENT_SOURCE_DIR}/md5.c
    ${CMAKE_CURRENT_SOURCE_DIR}/md2.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rmd160.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rmd128.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rmd256.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rmd320.c
    ${CMAKE_CURRENT_SOURCE_DIR}/sha3_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/sha3.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tiger.c
    ${CMAKE_CURRENT_SOURCE_DIR}/sha1.c
    ${CMAKE_CURRENT_SOURCE_DIR}/blake2s.c
    ${CMAKE_CURRENT_SOURCE_DIR}/blake2b.c
)

#-----------------------------------------------------------------------------
# Add subdirectories
#-----------------------------------------------------------------------------
add_subdirectory(sha2)
add_subdirectory(chc)
add_subdirectory(helper)
add_subdirectory(whirl)


#-----------------------------------------------------------------------------
# Hash
#-----------------------------------------------------------------------------
target_sources(${PROJECT_NAME}-shared PRIVATE ${HASH_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${HASH_SOURCES})
