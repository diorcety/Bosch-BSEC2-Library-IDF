idf_component_register(
  SRCS "lib/src/bsec2.cpp" "lib/src/commMux/commMux.cpp"
  INCLUDE_DIRS "lib/src/inc" "lib/src"
  REQUIRES Bosch-BME68x-Library
)

set(cpu ${IDF_TARGET})
if(cpu MATCHES "^esp32" AND NOT cpu MATCHES "^esp32s" AND NOT cpu STREQUAL "esp32")
    set(cpu "esp32c3")
endif()
message(STATUS "CPU variant: ${cpu}")
target_link_libraries(${COMPONENT_LIB} PRIVATE "${CMAKE_CURRENT_LIST_DIR}/lib/src/${cpu}/libalgobsec.a")

