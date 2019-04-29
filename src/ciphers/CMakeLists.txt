set(CIPHERS_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/aes/aes_tab.c
    ${CMAKE_CURRENT_SOURCE_DIR}/aes/aes.c
    ${CMAKE_CURRENT_SOURCE_DIR}/safer/safer_tab.c
    ${CMAKE_CURRENT_SOURCE_DIR}/safer/safer.c
    ${CMAKE_CURRENT_SOURCE_DIR}/safer/saferp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/twofish/twofish_tab.c
    ${CMAKE_CURRENT_SOURCE_DIR}/twofish/twofish.c
    ${CMAKE_CURRENT_SOURCE_DIR}/anubis.c
    ${CMAKE_CURRENT_SOURCE_DIR}/blowfish.c
    ${CMAKE_CURRENT_SOURCE_DIR}/camellia.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cast5.c
    ${CMAKE_CURRENT_SOURCE_DIR}/des.c
    ${CMAKE_CURRENT_SOURCE_DIR}/idea.c
    ${CMAKE_CURRENT_SOURCE_DIR}/kasumi.c
    ${CMAKE_CURRENT_SOURCE_DIR}/khazad.c
    ${CMAKE_CURRENT_SOURCE_DIR}/kseed.c
    ${CMAKE_CURRENT_SOURCE_DIR}/multi2.c
    ${CMAKE_CURRENT_SOURCE_DIR}/noekeon.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rc2.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rc5.c
    ${CMAKE_CURRENT_SOURCE_DIR}/rc6.c
    ${CMAKE_CURRENT_SOURCE_DIR}/serpent.c
    ${CMAKE_CURRENT_SOURCE_DIR}/skipjack.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xtea.c
)

add_library(ciphers_shared_obj OBJECT
    ${CIPHERS_SOURCES}
)

add_library(ciphers_static_obj OBJECT
    ${CIPHERS_SOURCES}
)

set_target_properties(ciphers_shared_obj PROPERTIES POSITION_INDEPENDENT_CODE TRUE)
