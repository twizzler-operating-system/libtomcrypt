set(PK_PKCS8_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/pkcs8_decode_flexi.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_PKCS8_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_PKCS8_SOURCES})
