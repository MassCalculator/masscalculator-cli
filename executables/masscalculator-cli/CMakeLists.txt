configure_file(config/software_version.h.in
  ${CMAKE_CURRENT_BINARY_DIR}/include/masscalculator/${PROJECT_NAME}/software_version.h)

add_executable(${PROJECT_NAME}
  masscalculator-cli.cc
)

target_include_directories(${PROJECT_NAME} PRIVATE 
  $<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}/include>
)

target_link_libraries(${PROJECT_NAME}
  PRIVATE
    masscalculator::masscalculator-core
)
