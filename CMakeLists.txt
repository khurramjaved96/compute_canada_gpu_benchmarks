#CC Build instructions
#module load python/3.7 and  module load scipy-stack and module load mariadb
#module load mariadb-connector-c

cmake_minimum_required(VERSION 3.14)
project(FlexibleNN LANGUAGES CUDA CXX)
#enable_language(CUDA)
enable_testing()

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_executable(CUDATest cuda_source_test.cu include/experiment/Experiment.h src/experiment/Experiment.cpp include/experiment/Database.h
        src/experiment/Database.cpp include/experiment/Metric.h src/experiment/Metric.cpp)

add_executable(CUDATestRandom cuda_random_memory_access.cu include/experiment/Experiment.h src/experiment/Experiment.cpp include/experiment/Database.h
        src/experiment/Database.cpp include/experiment/Metric.h src/experiment/Metric.cpp)

target_link_libraries(CUDATest PUBLIC tbb)
target_link_libraries(CUDATest PUBLIC mariadb)

target_link_libraries(CUDATestRandom PUBLIC tbb)
target_link_libraries(CUDATestRandom PUBLIC mariadb)

project(FlexibleNN LANGUAGES CXX)

