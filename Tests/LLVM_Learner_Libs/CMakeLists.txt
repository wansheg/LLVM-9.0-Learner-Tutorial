project(LLVM_Learner_Libs) 

set(Outputname "LLVM_Learner_Libs")

cmake_minimum_required(VERSION 3.10) 

find_package(LLVM REQUIRED CONFIG) 
find_package(Polly) 
find_package(Clang) 

message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}") 
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}") 

message(STATUS "Using PollyConfig.cmake in: ${Polly_CMAKE_DIR}") 
message(STATUS "Using ClangConfig.cmake in: ${CLANG_CMAKE_DIR}") 
# Needed to use support library 

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fno-rtti -std=c++14 -g") 

include_directories(${Clang_INCLUDE_DIRS}) 
include_directories(${LLVM_INCLUDE_DIRS}) 
include_directories(${Polly_INCLUDE_DIRS}) 

include_directories(./ ../../Implementations/ 
../../Implementations/HI_FindFunctions 
../../Implementations/HI_print 
../../Implementations/HI_LoopInFormationCollect 
../../Implementations/HI_DependenceList 
../../Implementations/HI_SysExec 
../../Implementations/HI_Polly_Info 
../../Implementations/HI_LoopDependenceAnalysis
../../Implementations/HI_SimpleTimingEvaluation
../../Implementations/HI_GEP_OffsetCombine
../../Implementations/HI_DuplicateInstRm
../../Implementations/HI_VarWidthReduce
../../Implementations/HI_SeparateConstOffsetFromGEP
../../Implementations/HI_APIntSrcAnalysis
../../Implementations/HI_NoDirectiveTimingResourceEvaluation
../../Implementations/HI_IntstructionMoveBackward
../../Implementations/HI_HLSDuplicateInstRm
../../Implementations/HI_AggressiveLSR_MUL
../../Implementations/HI_ArrayAccessPattern
../../Implementations/HI_WithDirectiveTimingResourceEvaluation
../../Implementations/HI_StringProcess
)

add_subdirectory(../../Implementations ./building)

