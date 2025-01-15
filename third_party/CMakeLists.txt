# @copyright See `LICENSE` in the root directory of this project.
# third_party/CMakeLists.txt


# Default FetchContent to Verbose. But don't override a user's explicit setting.
if(NOT FETCHCONTENT_QUIET)
  set(FETCHCONTENT_QUIET Off)
endif()


# Download CPM.cmake
file(
  DOWNLOAD      https://github.com/cpm-cmake/CPM.cmake/releases/download/v0.40.2/CPM.cmake ${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake
  EXPECTED_HASH SHA256=c8cdc32c03816538ce22781ed72964dc864b2a34a310d3b7104812a5ca2d835d
)
include(${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake)



macro(add_thirdparty dir)
  set(CMAKE_FOLDER "3rdparty/spdlog")
  # include() instead of add_subdirectory() so a 3rd party can modify the parent (global)
  # scope. Note how catch2 adds to
  include("${dir}/CMakeLists.in")
endmacro()


add_thirdparty(fmt)
add_thirdparty(spdlog)
add_thirdparty(sqlite)
add_thirdparty(cli11) # CLI11
add_thirdparty(boost) # ...and boost_sqlite
add_thirdparty(magic_enum)
add_thirdparty(google_benchmark) # benchmark
add_thirdparty(catch2)
