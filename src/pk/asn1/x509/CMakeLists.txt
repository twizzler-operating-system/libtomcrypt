set(PK_ASN1_X509_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/x509_encode_subject_public_key_info.c
    ${CMAKE_CURRENT_SOURCE_DIR}/x509_decode_subject_public_key_info.c
    ${CMAKE_CURRENT_SOURCE_DIR}/x509_decode_public_key_from_certificate.c
)

target_sources(${PROJECT_NAME}-shared PRIVATE ${PK_ASN1_X509_SOURCES})
target_sources(${PROJECT_NAME}-static PRIVATE ${PK_ASN1_X509_SOURCES})
