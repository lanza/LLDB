# targets added via add_llvm_utility get exported via llvm for LLVMConfig.cmake.
# So standalone builds of lldb can potentially import this via LLVMConfig and
# also attempt to build it in tree. So only build it if it doesn't exist
if (NOT TARGET lit-cpuid)
  add_llvm_utility(lit-cpuid
    lit-cpuid.cpp
    )

  target_link_libraries(lit-cpuid PRIVATE LLVMSupport)
  set_target_properties(lit-cpuid PROPERTIES FOLDER "lldb utils")
endif()
