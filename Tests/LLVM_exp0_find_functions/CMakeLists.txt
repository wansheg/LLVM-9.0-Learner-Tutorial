project(LLVM_exp0_find_functions) 

set(Outputname "LLVM_exp0_find_functions")

cmake_minimum_required(VERSION 3.10) 

find_package(LLVM REQUIRED CONFIG) 

message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}") 
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}") 

# Needed to use support library 

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fno-rtti -std=c++14") 

include_directories(${LLVM_INCLUDE_DIRS}) 
include_directories(./ ../../Implementations/ ../../Implementations/HI_FindFunctions ../../Implementations/HI_print)

link_directories("../LLVM_Learner_Libs")
set(MAKE_CMD "../../../BuildLibs.sh")
MESSAGE("COMMAND: ${MAKE_CMD} ")
execute_process(COMMAND ${MAKE_CMD}
   RESULT_VARIABLE CMD_ERROR
      OUTPUT_FILE CMD_OUTPUT)
add_definitions(${LLVM_DEFINITIONS}) 

add_executable(${Outputname} LLVM_exp0_find_functions.cc) 

llvm_map_components_to_libnames(llvm_libs support core irreader engine nativecodegen) 




target_link_libraries(${Outputname} pthread dl HI_FindFunctions HI_print) #link llvm component 

# set(llvm_libs "")

#link llvm library 
target_link_libraries(${Outputname} 
LLVMLTO 
LLVMPasses 
LLVMObjCARCOpts 
LLVMMIRParser 
LLVMSymbolize 
LLVMDebugInfoPDB 
LLVMDebugInfoDWARF 
LLVMCoverage 
LLVMMCA 
LLVMTableGen 
LLVMDlltoolDriver 
LLVMXRay 
LLVMOrcJIT 
LLVMXCoreDisassembler 
LLVMXCoreCodeGen 
LLVMXCoreDesc 
LLVMXCoreInfo 
LLVMXCoreAsmPrinter 
LLVMWebAssemblyDisassembler 
LLVMWebAssemblyCodeGen 
LLVMWebAssemblyDesc 
LLVMWebAssemblyAsmPrinter 
LLVMWebAssemblyAsmParser 
LLVMWebAssemblyInfo 
LLVMSystemZDisassembler 
LLVMSystemZCodeGen 
LLVMSystemZAsmParser 
LLVMSystemZDesc 
LLVMSystemZInfo 
LLVMSystemZAsmPrinter 
LLVMSparcDisassembler 
LLVMSparcCodeGen 
LLVMSparcAsmParser 
LLVMSparcDesc 
LLVMSparcInfo 
LLVMSparcAsmPrinter 
LLVMPowerPCDisassembler 
LLVMPowerPCCodeGen 
LLVMPowerPCAsmParser 
LLVMPowerPCDesc 
LLVMPowerPCInfo 
LLVMPowerPCAsmPrinter 
LLVMNVPTXCodeGen 
LLVMNVPTXDesc 
LLVMNVPTXInfo 
LLVMNVPTXAsmPrinter 
LLVMMSP430Disassembler 
LLVMMSP430CodeGen 
LLVMMSP430AsmParser 
LLVMMSP430Desc 
LLVMMSP430Info 
LLVMMSP430AsmPrinter 
LLVMMipsDisassembler 
LLVMMipsCodeGen 
LLVMMipsAsmParser 
LLVMMipsDesc 
LLVMMipsInfo 
LLVMMipsAsmPrinter 
LLVMLanaiDisassembler 
LLVMLanaiCodeGen 
LLVMLanaiAsmParser 
LLVMLanaiDesc 
LLVMLanaiAsmPrinter 
LLVMLanaiInfo 
LLVMHexagonDisassembler 
LLVMHexagonCodeGen 
LLVMHexagonAsmParser 
LLVMHexagonDesc 
LLVMHexagonInfo 
LLVMBPFDisassembler 
LLVMBPFCodeGen 
LLVMBPFAsmParser 
LLVMBPFDesc 
LLVMBPFInfo 
LLVMBPFAsmPrinter 
LLVMARMDisassembler 
LLVMARMCodeGen 
LLVMARMAsmParser 
LLVMARMDesc 
LLVMARMInfo 
LLVMARMAsmPrinter 
LLVMARMUtils 
LLVMAMDGPUDisassembler 
LLVMAMDGPUCodeGen 
LLVMAMDGPUAsmParser 
LLVMAMDGPUDesc 
LLVMAMDGPUInfo 
LLVMAMDGPUAsmPrinter 
LLVMAMDGPUUtils 
LLVMAArch64Disassembler 
LLVMAArch64CodeGen 
LLVMAArch64AsmParser 
LLVMAArch64Desc 
LLVMAArch64Info 
LLVMAArch64AsmPrinter 
LLVMAArch64Utils 
LLVMObjectYAML 
LLVMLibDriver 
LLVMOption 
LLVMOptRemarks 
LLVMWindowsManifest 
LLVMTextAPI 
LLVMFuzzMutate 
LLVMX86Disassembler 
LLVMX86AsmParser 
LLVMX86CodeGen 
LLVMGlobalISel 
LLVMSelectionDAG 
LLVMAsmPrinter 
LLVMX86Desc 
LLVMMCDisassembler 
LLVMX86Info 
LLVMX86AsmPrinter 
LLVMX86Utils 
LLVMMCJIT 
LLVMLineEditor 
LLVMInterpreter 
LLVMExecutionEngine 
LLVMRuntimeDyld 
LLVMCodeGen 
LLVMTarget 
LLVMCoroutines 
LLVMipo 
LLVMInstrumentation 
LLVMVectorize 
LLVMScalarOpts 
LLVMLinker 
LLVMIRReader 
LLVMAsmParser 
LLVMInstCombine 
LLVMBitWriter 
LLVMAggressiveInstCombine 
LLVMTransformUtils 
LLVMAnalysis 
LLVMProfileData 
LLVMObject 
LLVMMCParser 
LLVMMC 
LLVMDebugInfoCodeView 
LLVMDebugInfoMSF 
LLVMBitReader 
LLVMCore 
LLVMBinaryFormat 
LLVMSupport 
LLVMDemangle
) 

# message(STATUS "LLVM Libraries0 are: ${llvm_libs}") 
# message(STATUS "LLVM Libraries1 are: ${ARG_LINK_COMPONENTS}") 
# message(STATUS "LLVM Libraries2 are: ${LLVM_LINK_COMPONENTS}") 
# message(STATUS "LLVM Definitions are: ${LLVM_PACKAGE_VERSION}") 
