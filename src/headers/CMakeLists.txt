list(APPEND PUBLIC_HEADERS
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_argchk.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_cfg.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_cipher.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_custom.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_hash.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_mac.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_macros.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_math.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_misc.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_pkcs.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_pk.h
    ${CMAKE_CURRENT_SOURCE_DIR}/tomcrypt_prng.h
)

set_property(GLOBAL PROPERTY PUBLIC_HEADERS ${PUBLIC_HEADERS})
