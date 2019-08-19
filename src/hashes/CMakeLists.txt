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

set(HASH_SOURCES)

set(HASH_MD_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/md4.c
    ${CMAKE_CURRENT_SOURCE_DIR}/md5.c
    ${CMAKE_CURRENT_SOURCE_DIR}/md2.c
)

set(HASH_RMD_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/rmd160.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rmd128.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rmd256.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rmd320.c
)

set(HASH_SHA3_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/sha3_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/sha3.c
)

set(HASH_TIGER_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/tiger.c
)

set(HASH_SHA1_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/sha1.c
)

set(HASH_BLAKE_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/blake2s.c
    ${CMAKE_CURRENT_SOURCE_DIR}/blake2b.c
)

if(ENABLE_HASH_MD)
    list(APPEND HASH_SOURCES ${HASH_MD_SOURCES})
endif()

if(ENABLE_HASH_RMD)
    list(APPEND HASH_SOURCES ${HASH_RMD_SOURCES})
endif()

if(ENABLE_HASH_SHA1)
    list(APPEND HASH_SOURCES ${HASH_SHA1_SOURCES})
endif()

if(ENABLE_HASH_SHA3)
    list(APPEND HASH_SOURCES ${HASH_SHA3_SOURCES})
endif()

if(ENABLE_HASH_TIGER)
    list(APPEND HASH_SOURCES ${HASH_TIGER_SOURCES})
endif()

if(ENABLE_HASH_BLAKE)
    list(APPEND HASH_SOURCES ${HASH_BLAKE_SOURCES})
endif()

if(ENABLE_HASH_SHA2)
    add_subdirectory(sha2)
    list(APPEND HASH_SOURCES ${HASH_SHA2_SOURCES})
endif()

if(ENABLE_HASH_CHC)
    add_subdirectory(chc)
    list(APPEND HASH_SOURCES ${HASH_CHC_SOURCES})
endif()

if(ENABLE_HASH_HELPER)
    add_subdirectory(helper)
    list(APPEND HASH_SOURCES ${HASH_HELPER_SOURCES})
endif()

if(ENABLE_HASH_WHIRL)
    add_subdirectory(whirl)
    list(APPEND HASH_SOURCES ${HASH_WHIRL_SOURCES})
endif()

#-----------------------------------------------------------------------------
# Hash
#-----------------------------------------------------------------------------
target_sources(${PROJECT_NAME}-shared PRIVATE ${HASH_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${HASH_SOURCES})
