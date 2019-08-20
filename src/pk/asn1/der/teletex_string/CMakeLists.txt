set(PK_ASN1_DER_TELETEX_STRING_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_teletex_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_teletex_string.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_TELETEX_STRING_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_TELETEX_STRING_SOURCES})
