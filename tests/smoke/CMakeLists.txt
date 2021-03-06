# Copyright (c) 2017-2019, Lawrence Livermore National Security, LLC and
# other BLT Project Developers. See the top-level COPYRIGHT file for details
# 
# SPDX-License-Identifier: (BSD-3-Clause)

#
# Smoke tests for BLT TPLs
#

################
# gtest test
################
if(ENABLE_GTEST)
    blt_add_executable(NAME blt_gtest_smoke
                       SOURCES blt_gtest_smoke.cpp
                       OUTPUT_DIR ${TEST_OUTPUT_DIRECTORY}
                       DEPENDS_ON gtest
                       FOLDER blt/tests )

    blt_add_test( NAME blt_gtest_smoke
                  COMMAND blt_gtest_smoke)
endif()

################
# gmock test
################
if(ENABLE_GMOCK)
    blt_add_executable(NAME blt_gmock_smoke
                       SOURCES blt_gmock_smoke.cpp
                       OUTPUT_DIR ${TEST_OUTPUT_DIRECTORY}
                       DEPENDS_ON gtest gmock
                       FOLDER blt/tests )

    blt_add_test( NAME blt_gmock_smoke
                  COMMAND blt_gmock_smoke)
endif()


################
# gbenchmark test
################
if (ENABLE_BENCHMARKS)
    blt_add_executable(NAME blt_gbenchmark_smoke
                       SOURCES blt_gbenchmark_smoke.cpp
                       OUTPUT_DIR ${TEST_OUTPUT_DIRECTORY}
                       DEPENDS_ON gbenchmark
                       FOLDER blt/benchmarks )

    blt_add_benchmark( NAME blt_gbenchmark_smoke 
                       COMMAND  blt_gbenchmark_smoke "--benchmark_min_time=0.0001")
endif()


################
# fruit test
################
if (ENABLE_FORTRAN AND ENABLE_FRUIT)
    blt_add_executable(NAME blt_fruit_smoke
                       SOURCES blt_fruit_smoke.f90
                       OUTPUT_DIR ${TEST_OUTPUT_DIRECTORY}
                       DEPENDS_ON fruit
                       FOLDER blt/tests )

    blt_add_test(NAME blt_fruit_smoke
                 COMMAND blt_fruit_smoke)
endif()


################
# OpenMP test
################
if (ENABLE_OPENMP)
    blt_add_executable(NAME blt_openmp_smoke 
                       SOURCES blt_openmp_smoke.cpp 
                       OUTPUT_DIR ${TEST_OUTPUT_DIRECTORY}
                       DEPENDS_ON openmp
                       FOLDER blt/tests )

    blt_add_test(NAME blt_openmp_smoke
                 COMMAND blt_openmp_smoke)
endif()


################
#  MPI test
################
if (ENABLE_MPI)
    blt_add_executable(NAME blt_mpi_smoke
                       SOURCES blt_mpi_smoke.cpp
                       OUTPUT_DIR ${TEST_OUTPUT_DIRECTORY} 
                       DEPENDS_ON mpi
                       FOLDER blt/tests )

    blt_add_test(NAME blt_mpi_smoke
                 COMMAND blt_mpi_smoke
                 NUM_MPI_TASKS 2)
endif()

################
#  CUDA test
################
if (ENABLE_CUDA)
    blt_add_executable(NAME blt_cuda_smoke
                       SOURCES blt_cuda_smoke.cpp
                       OUTPUT_DIR ${TEST_OUTPUT_DIRECTORY} 
                       DEPENDS_ON cuda
                       FOLDER blt/tests )

    blt_add_test(NAME blt_cuda_smoke
                 COMMAND blt_cuda_smoke)

    blt_add_executable(NAME blt_cuda_runtime_smoke
                       SOURCES blt_cuda_runtime_smoke.cpp
                       OUTPUT_DIR ${TEST_OUTPUT_DIRECTORY} 
                       DEPENDS_ON cuda_runtime
                       FOLDER blt/tests )

    blt_add_test(NAME blt_cuda_runtime_smoke
                 COMMAND blt_cuda_runtime_smoke)


endif()

################
#  ROCM test
################
if (ENABLE_ROCM)
    blt_add_executable(NAME blt_rocm_smoke
                       SOURCES blt_rocm_smoke.cpp
                       OUTPUT_DIR ${TEST_OUTPUT_DIRECTORY}
                       DEPENDS_ON rocm
                       FOLDER blt/tests )

    blt_add_test(NAME blt_rocm_smoke
                 COMMAND blt_rocm_smoke)

    blt_add_executable(NAME blt_rocm_runtime_smoke
                       SOURCES blt_rocm_runtime_smoke.cpp
                       OUTPUT_DIR ${TEST_OUTPUT_DIRECTORY}
                       DEPENDS_ON rocm
                       FOLDER blt/tests )

    blt_add_test(NAME blt_rocm_runtime_smoke
                 COMMAND blt_rocm_runtime_smoke)


endif()

