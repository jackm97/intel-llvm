set(LLVM_LINK_COMPONENTS BitWriter BitReader Core Object Support TransformUtils TargetParser)

add_clang_tool(clang-offload-wrapper
  ClangOffloadWrapper.cpp
  SymPropReader.cpp

  DEPENDS
  intrinsics_gen
  )

set(CLANG_OFFLOAD_WRAPPER_LIB_DEPS
  clangBasic
  LLVMSupport
  )

add_dependencies(clang clang-offload-wrapper)

clang_target_link_libraries(clang-offload-wrapper
  PRIVATE
  ${CLANG_OFFLOAD_WRAPPER_LIB_DEPS}
  )
