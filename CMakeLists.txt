cmake_minimum_required(VERSION 3.12)

project("Solid Wall Of C++ Library")
set(INSTALL_DIR ${CMAKE_HOME_DIRECTORY})

# Fortunately this has no external dependencies so the set up can be simple.
add_subdirectory(code)
add_subdirectory(unit_tests)
add_subdirectory(example)
add_subdirectory(doc EXCLUDE_FROM_ALL)

# Find all of the directories subject to clang formatting and make a target to do the format.
set(_CLANG_DIRS "")
get_target_property(_TMP libswoc CLANG_FORMAT_DIRS)
list(APPEND _CLANG_DIRS ${_TMP})
get_target_property(_TMP test_libswoc CLANG_FORMAT_DIRS)
list(APPEND _CLANG_DIRS ${_TMP})
list(JOIN _CLANG_DIRS " " _CLANG_DIRS)

#add_custom_target(clang-format COMMAND ${CMAKE_HOME_DIRECTORY}/tools/clang-format.sh ${_CLANG_DIRS})
#add_custom_target(clang-format COMMAND clang-format ${_CLANG_DIRS})
