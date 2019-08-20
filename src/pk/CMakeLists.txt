#-----------------------------------------------------------------------------
# Pk options
#-----------------------------------------------------------------------------
option(ENABLE_PK_ASN1_DER "Enable asn1 der" TRUE)
option(ENABLE_PK_ASN1_OID "Enable asn1 iod" TRUE)
option(ENABLE_PK_ASN1_X509 "Enable asn1 x509" TRUE)
option(ENABLE_PK_DH "Enable dh" TRUE)
option(ENABLE_PK_DSA "Enable dsa" TRUE)
option(ENABLE_PK_ECC "Enable ecc" TRUE)
option(ENABLE_PK_PKCS1 "Enable pkcs1" TRUE)
option(ENABLE_PK_RSA "Enable rsa" TRUE)
option(ENABLE_PK_PKCS8 "Enable pkcs8" TRUE)

#-----------------------------------------------------------------------------
# Add subdirectories
#-----------------------------------------------------------------------------
if(ENABLE_PK_ASN1_DER)
    add_subdirectory(asn1/der/bit)
    add_subdirectory(asn1/der/boolean)
    add_subdirectory(asn1/der/choice)
    add_subdirectory(asn1/der/custom_type)
    add_subdirectory(asn1/der/general)
    add_subdirectory(asn1/der/generalizedtime)
    add_subdirectory(asn1/der/ia5)
    add_subdirectory(asn1/der/integer)
    add_subdirectory(asn1/der/object_identifier)
    add_subdirectory(asn1/der/octet)
    add_subdirectory(asn1/der/printable_string)
    add_subdirectory(asn1/der/sequence)
    add_subdirectory(asn1/der/set)
    add_subdirectory(asn1/der/short_integer)
    add_subdirectory(asn1/der/teletex_string)
    add_subdirectory(asn1/der/utctime)
    add_subdirectory(asn1/der/utf8)
endif()

if(ENABLE_PK_ASN1_OID)
    add_subdirectory(asn1/oid)
endif()

if(ENABLE_PK_PKCS8)
    add_subdirectory(asn1/pkcs8)
endif()

if(ENABLE_PK_ASN1_X509)
    add_subdirectory(asn1/x509)
endif()

if(ENABLE_PK_DH)
    add_subdirectory(dh)
endif()

if(ENABLE_PK_DSA)
    add_subdirectory(dsa)
endif()

if(ENABLE_PK_ECC)
    add_subdirectory(ecc)
endif()

if(ENABLE_PK_PKCS1)
    add_subdirectory(pkcs1)
endif()

if(ENABLE_PK_RSA)
    add_subdirectory(rsa)
endif()
