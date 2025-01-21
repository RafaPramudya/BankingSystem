cmake_minimum_required(VERSION 3.10)
project(BankingSystem VERSION 0.1.0 LANGUAGES C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_SOURCE_DIR}/Release)

include_directories(include)

add_executable(BankingSystem src/main.c)

if (CMAKE_BUILD_TYPE STREQUAL "Release")
    if (CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
        target_compile_options(BankingSystem PRIVATE /O2 /MP)
    elseif(CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
        target_compile_options(BankingSystem PRIVATE -O3 -march=native)
    endif()
endif()