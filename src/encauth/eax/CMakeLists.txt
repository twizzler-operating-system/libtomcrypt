set(ENCAUTH_EAX_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/eax_decrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/eax_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/eax_done.c
    ${CMAKE_CURRENT_SOURCE_DIR}/eax_decrypt_verify_memory.c
    ${CMAKE_CURRENT_SOURCE_DIR}/eax_init.c
    ${CMAKE_CURRENT_SOURCE_DIR}/eax_encrypt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/eax_encrypt_authenticate_memory.c
    ${CMAKE_CURRENT_SOURCE_DIR}/eax_addheader.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${ENCAUTH_EAX_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${ENCAUTH_EAX_SOURCES})
