###############################################################################
# SOURCES
###############################################################################

file(GLOB_RECURSE SOURCES RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.cpp)

###############################################################################
# INSTALL
###############################################################################

add_library(${PROJECT_NAME} ${SOURCES})

target_include_directories(
  ${PROJECT_NAME}
  INTERFACE
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
)

target_link_libraries(
  ${PROJECT_NAME}
  PUBLIC
    ecl_errors::ecl_errors
    ecl_geometry::ecl_geometry
    ecl_math::ecl_math
    ecl_formatters::ecl_formatters
    ecl_linear_algebra::ecl_linear_algebra
)

set_target_properties(${PROJECT_NAME}
  PROPERTIES
    SOVERSION ${${PROJECT_NAME}_VERSION}
    VERSION ${${PROJECT_NAME}_VERSION}
)

install(TARGETS ${PROJECT_NAME} EXPORT ${PROJECT_NAME}
   RUNTIME DESTINATION bin
   ARCHIVE DESTINATION lib
   LIBRARY DESTINATION lib
)
