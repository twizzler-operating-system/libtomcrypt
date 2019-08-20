set(MISC_SSH_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/ssh_decode_sequence_multi.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ssh_encode_sequence_multi.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${MISC_SSH_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${MISC_SSH_SOURCES})
