set(PRNGS_SOURCES
    sprng.c
#     sober128.c
#     rc4.c
    rng_get_bytes.c
    rng_make_prng.c
#     chacha20.c
#     fortuna.c
#     yarrow.c
)

#-----------------------------------------------------------------------------
# PRNGS
#-----------------------------------------------------------------------------
add_library(prngs_shared_obj OBJECT
    ${PRNGS_SOURCES}
)

add_library(prngs_static_obj OBJECT
    ${PRNGS_SOURCES}
)

set_target_properties(prngs_shared_obj PROPERTIES POSITION_INDEPENDENT_CODE TRUE)
