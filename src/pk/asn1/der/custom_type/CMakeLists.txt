set(PK_ASN1_DER_CUSTOM_TYPE_SOURCES
    der_encode_custom_type.c
    der_decode_custom_type.c
    der_length_custom_type.c
)

#-----------------------------------------------------------------------------
# ASN1 DER CUSTOM TYPE
#-----------------------------------------------------------------------------
add_library(pk_asn1_der_custom_type_shared_obj OBJECT
    ${PK_ASN1_DER_CUSTOM_TYPE_SOURCES}
)

add_library(pk_asn1_der_custom_type_static_obj OBJECT
    ${PK_ASN1_DER_CUSTOM_TYPE_SOURCES}
)

set_target_properties(pk_asn1_der_custom_type_shared_obj PROPERTIES POSITION_INDEPENDENT_CODE TRUE)
