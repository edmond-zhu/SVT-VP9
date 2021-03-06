﻿# ~~~
# Copyright(c) 2019 Intel Corporation
# SPDX - License - Identifier: BSD - 2 - Clause - Patent
# ~~~

# ASM_SSE2 Directory CMakeLists.txt

# Include Encoder Subdirectories
include_directories(${PROJECT_SOURCE_DIR}/Source/API
                    ${PROJECT_SOURCE_DIR}/Source/Lib/Codec
                    ${PROJECT_SOURCE_DIR}/Source/Lib/C_DEFAULT
                    ${PROJECT_SOURCE_DIR}/Source/Lib/ASM_SSE2
                    ${PROJECT_SOURCE_DIR}/Source/Lib/VPX)

set(flags_to_test -msse2)

if(CMAKE_C_COMPILER_ID STREQUAL "Intel" AND NOT WIN32)
    list(APPEND flags_to_test -static-intel -w)
endif()

test_apply_compiler_flags(${flags_to_test})

file(GLOB
     all_files
     "*.h"
     "*.c"
     "*.asm")

add_library(VP9_ASM_SSE2 OBJECT ${all_files})
