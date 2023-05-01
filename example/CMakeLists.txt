cmake_minimum_required(VERSION 3.3 FATAL_ERROR)


#find_package(TensorflowCC REQUIRED)
set(CMAKE_VERBOSE_MAKEFILE ON)
link_directories($ENV{CONDA_PREFIX}/lib)
include_directories($ENV{CONDA_PREFIX}/include)
add_executable(example example.cpp)
target_link_libraries(example tensorflow_cc tensorflow_framework)
#target_link_libraries(example tensorflow_cc tensorflow_framework)
# link cuda if it is available
find_package(CUDA)
if(CUDA_FOUND)
  target_link_libraries(example ${CUDA_LIBRARIES})
endif()
