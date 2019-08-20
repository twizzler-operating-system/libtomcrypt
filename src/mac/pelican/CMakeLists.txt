set(MAC_PELICAN_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/pelican_memory.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pelican_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/pelican.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MAC_PELICAN_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MAC_PELICAN_SOURCES})
