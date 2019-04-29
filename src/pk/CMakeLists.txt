set(PK_SOURCES)

if(ENABLE_PK_ASN1_DER)
    add_subdirectory(asn1/der/bit)
    add_subdirectory(asn1/der/boolean)
    add_subdirectory(asn1/der/choice)
#     add_subdirectory(asn1/der/custom_type)
#     add_subdirectory(asn1/der/general)
    add_subdirectory(asn1/der/generalizedtime)
    add_subdirectory(asn1/der/ia5)
    add_subdirectory(asn1/der/integer)
    add_subdirectory(asn1/der/object_identifier)
    add_subdirectory(asn1/der/octet)
    add_subdirectory(asn1/der/printable_string)
    add_subdirectory(asn1/der/sequence)
#     add_subdirectory(asn1/der/set)
    add_subdirectory(asn1/der/short_integer)
    add_subdirectory(asn1/der/teletex_string)
    add_subdirectory(asn1/der/utctime)
    add_subdirectory(asn1/der/utf8)

    list(APPEND PK_SOURCES ${PK_ASN1_DER_BIT_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_BOOLEAN_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_CHOICE_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_CUSTOM_TYPE_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_GENERAL_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_GENERALIZEDTIME_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_IA5_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_INTEGER_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_OBJECT_IDENTIFIER_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_OCTET_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_PRINTABLE_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_SEQUENCE_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_SET_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_SHORT_INTEGER_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_TELETEX_STRING_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_UTCTIME_SOURCES})
    list(APPEND PK_SOURCES ${PK_ASN1_DER_UTF8_SOURCES})
endif()

if(ENABLE_PK_ASN1_X509)
    add_subdirectory(asn1/x509)
    list(APPEND PK_SOURCES ${PK_ASN1_X509_SOURCES})
endif()

if(ENABLE_PK_DH)
    add_subdirectory(dh)
    list(APPEND PK_SOURCES ${PK_DH_SOURCES})
endif()

if(ENABLE_PK_DSA)
    add_subdirectory(dsa)
    list(APPEND PK_SOURCES ${PK_DSA_SOURCES})
endif()

if(ENABLE_PK_ECC)
    add_subdirectory(ecc)
    list(APPEND PK_SOURCES ${PK_ECC_SOURCES})
endif()

if(ENABLE_PK_PKCS1)
    add_subdirectory(pkcs1)
    list(APPEND PK_SOURCES ${PK_PKCS1_SOURCES})
endif()

if(ENABLE_PK_RSA)
    add_subdirectory(rsa)
    list(APPEND PK_SOURCES ${PK_RSA_SOURCES})
endif()

#-----------------------------------------------------------------------------
# Pk
#-----------------------------------------------------------------------------
add_library(pk_shared_obj OBJECT
    ${PK_SOURCES}
)

add_library(pk_static_obj OBJECT
    ${PK_SOURCES}
)

set_target_properties(pk_shared_obj PROPERTIES POSITION_INDEPENDENT_CODE TRUE)
