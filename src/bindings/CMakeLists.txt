##############################################################################
# Sources
##############################################################################

# api module
pybind11_add_module(api_py
  api_py.cc
)

set_target_properties(api_py PROPERTIES OUTPUT_NAME "api")

target_include_directories(api_py
  PUBLIC
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/src>
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
)

target_link_libraries(api_py
  PRIVATE
    maliput_object::api
    maliput::math
    pybind11::module
)

##############################################################################
# Install
##############################################################################

install(TARGETS api_py
  DESTINATION "${PYTHON_INSTALL_DIR}/maliput_object"
)
