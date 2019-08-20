set(PK_ASN1_DER_GENERAL_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_asn1_identifier.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_asn1_length.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_asn1_maps.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_asn1_length.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_asn1_length.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_asn1_identifier.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_asn1_identifier.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_GENERAL_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_GENERAL_SOURCES})
