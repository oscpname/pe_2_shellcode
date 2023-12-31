cmake_minimum_required ( VERSION 3.0 )

# replace "peconv_project" by your own project name:
project ( pe_to_shellcode )

option (PE2SHC_BUILD_TESTING "enable testing" OFF)

# libs
# modules:
set ( M_PARSER "libpeconv/libpeconv" )

# modules paths:
set (PECONV_DIR "${CMAKE_SOURCE_DIR}/${M_PARSER}" CACHE PATH "PEConv main path")
add_subdirectory ( ${PECONV_DIR} )
set ( PECONV_LIB $<TARGET_FILE:libpeconv> CACHE PATH "PEConvLib library path" )

# Add sub-directories
#
add_subdirectory ( pe2shc )
add_subdirectory ( runshc )
add_subdirectory ( injector )

# Setup testing
if(PE2SHC_BUILD_TESTING)
	enable_testing()
	add_subdirectory ( tests )
endif()
