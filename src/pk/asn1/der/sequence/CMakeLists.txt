set(PK_ASN1_DER_SEQUENCE_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_sequence_flexi.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_sequence_ex.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_sequence_ex.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_sequence_shrink.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_encode_sequence_multi.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_decode_sequence_multi.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_length_sequence.c
    ${CMAKE_CURRENT_SOURCE_DIR}/der_sequence_free.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_DER_SEQUENCE_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_DER_SEQUENCE_SOURCES})
