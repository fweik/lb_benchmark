function(BENCHMARK)
  cmake_parse_arguments(BENCHMARK "" "NAME" "SRC" ${ARGN})
  set(BENCHMARK_NAME BM_${BENCHMARK_NAME})
  add_executable(${BENCHMARK_NAME} ${BENCHMARK_SRC})
  target_link_libraries(${BENCHMARK_NAME} PRIVATE benchmark)
  target_include_directories(${BENCHMARK_NAME} PRIVATE ${CMAKE_SOURCE_DIR}/libs/benchmark/include ${CMAKE_SOURCE_DIR}/src)
endfunction(BENCHMARK)

BENCHMARK(NAME lb_mode_calculation SRC lb_mode_transformation.cpp)
