set(PK_ASN1_DER_IA5_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_ia5_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_ia5_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_ia5_string.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_IA5_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_IA5_SOURCES})
