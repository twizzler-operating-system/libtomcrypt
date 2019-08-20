set(STREAM_SALSA20_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/salsa20_crypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/salsa20_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/salsa20_ivctr64.c
    ${CMAKE_CURRENT_SOURCE_DIR}/salsa20_keystream.c
    ${CMAKE_CURRENT_SOURCE_DIR}/salsa20_memory.c
    ${CMAKE_CURRENT_SOURCE_DIR}/salsa20_setup.c
    ${CMAKE_CURRENT_SOURCE_DIR}/salsa20_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xsalsa20_memory.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xsalsa20_setup.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xsalsa20_test.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${STREAM_SALSA20_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${STREAM_SALSA20_SOURCES})
