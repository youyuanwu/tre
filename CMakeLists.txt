project(tre)

cmake_minimum_required(VERSION 3.16)

project (tre LANGUAGES C)

file(GLOB LIB_SOURCES
    lib/*.c
    lib/*.h
)

# this is duplicated
list(REMOVE_ITEM LIB_SOURCES ${tre_SOURCE_DIR}/lib/tre.h)

file(GLOB INCLUDE_SOURCES
    include/tre/*.h
    win32/config.h
)

# message("debug ${LIB_SOURCES}")
# message("debug ${INCLUDE_SOURCES}")

add_library(tre
    ${LIB_SOURCES} ${INCLUDE_SOURCES}
)

target_include_directories(tre
    PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include/tre
    PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/win32
)

target_compile_definitions(tre
    PRIVATE HAVE_CONFIG_H=1
)