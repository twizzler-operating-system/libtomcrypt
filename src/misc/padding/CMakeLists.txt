set(MISC_PADDING_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/padding_depad.c
    ${CMAKE_CURRENT_SOURCE_DIR}/padding_pad.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MISC_PADDING_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MISC_PADDING_SOURCES})
