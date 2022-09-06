add_mlir_dialect(Test test)

set(LLVM_TARGET_DEFINITIONS Test.td)

add_mlir_dialect_library(MLIRTest
        TestDialect.cpp
        Ops.cpp

        LINK_COMPONENTS
        Core

        LINK_LIBS PUBLIC
        MLIRIR
        MLIRSupport)