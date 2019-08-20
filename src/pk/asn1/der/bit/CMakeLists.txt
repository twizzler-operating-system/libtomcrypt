set(PK_ASN1_DER_BIT_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_raw_bit_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_bit_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_raw_bit_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_bit_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_bit_string.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_BIT_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_BIT_SOURCES})
