find_package(masscalculator-core CONFIG REQUIRED)

configure_file(config/software_version.h.in
  ${CMAKE_CURRENT_BINARY_DIR}/include/masscalculator/${PROJECT_NAME}/software_version.h)

add_executable(${PROJECT_NAME}
  masscalculator-cli.cc
)

target_include_directories(${PROJECT_NAME} PUBLIC 
  $<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}/include>
)


target_link_libraries(${PROJECT_NAME}
  PUBLIC
    masscalculator::masscalculator-core
)
