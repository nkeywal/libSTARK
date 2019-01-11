cmake_minimum_required(VERSION 3.1)
project(libSTARK)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fopenmp")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -maes")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -msse4")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -mpclmul")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -mtune=native")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fmessage-length=0")

add_library(algebralib
        algebra/algebralib/headers/algebraLib/AffinePolynomial.hpp
        algebra/algebralib/headers/algebraLib/AffineSpace.hpp
        algebra/algebralib/headers/algebraLib/BitExtract.hpp
        algebra/algebralib/headers/algebraLib/CircuitPolynomial.hpp
        algebra/algebralib/headers/algebraLib/ErrorHandling.hpp
        algebra/algebralib/headers/algebraLib/FFT.hpp
        algebra/algebralib/headers/algebraLib/FieldElement.hpp
        algebra/algebralib/headers/algebraLib/LinearizedPolynomial.hpp
        algebra/algebralib/headers/algebraLib/LinearPolynomial.hpp
        algebra/algebralib/headers/algebraLib/MappingsSys.hpp
        algebra/algebralib/headers/algebraLib/novelFFT.hpp
        algebra/algebralib/headers/algebraLib/PolynomialDegree.hpp
        algebra/algebralib/headers/algebraLib/PolynomialInterface.hpp
        algebra/algebralib/headers/algebraLib/SelectorSum.hpp
        algebra/algebralib/headers/algebraLib/SubspacePolynomial.hpp
        algebra/algebralib/headers/algebraLib/UnivariatePolynomialGeneral.hpp
        algebra/algebralib/headers/algebraLib/variable.hpp
        algebra/algebralib/headers/algebraLib/variable_operators.hpp
        algebra/algebralib/src/AffinePolynomial.cpp
        algebra/algebralib/src/AffineSpace.cpp
        algebra/algebralib/src/BitExtract.cpp
        algebra/algebralib/src/CircuitPolynomial.cpp
        algebra/algebralib/src/ErrorHandling.cpp
        algebra/algebralib/src/FFT.cpp
        algebra/algebralib/src/FieldElement.cpp
        algebra/algebralib/src/LinearPolynomial.cpp
        algebra/algebralib/src/MappingsSys.cpp
        algebra/algebralib/src/novelFFT.cpp
        algebra/algebralib/src/PolynomialDegree.cpp
        algebra/algebralib/src/SelectorSum.cpp
        algebra/algebralib/src/SubspacePolynomial.cpp
        algebra/algebralib/src/UnivariatePolynomialGeneral.cpp
        algebra/algebralib/src/variable.cpp
        )

add_executable(algebralib-tests
        algebra/algebralib-tests/CircuitPolynomial_UTEST.cpp
        algebra/algebralib-tests/FFT_UTEST.cpp
        algebra/algebralib-tests/FieldElement_UTEST.cpp
        algebra/algebralib-tests/LinearizedPolynomials_UTEST.cpp
        algebra/algebralib-tests/LinearPolynomial_UTEST.cpp
        algebra/algebralib-tests/main.cpp
        algebra/algebralib-tests/SelectorSum_UTEST.cpp
        algebra/algebralib-tests/UnivariatePolynomialGeneral_UTEST.cpp
        algebra/algebralib-tests/variable_UTEST.cpp
        )

include_directories(algebra/algebralib/headers)
include_directories(algebra/algebralib/headers/algebraLib)
include_directories(algebra/FFT/src)
include_directories(libstark/src/common/Algebra)
include_directories(libstark/src/common/Infrastructure)
include_directories(libstark/src/common/langCommon)
include_directories(libstark/src/common/Utils)
include_directories(libstark/src/languages/Acsp)
include_directories(libstark/src/languages/Bair)
include_directories(libstark/src/protocols)
include_directories(libstark/src/protocols/Ali)
include_directories(libstark/src/protocols/Ali/common_details)
include_directories(libstark/src/protocols/Ali/verifier_details)
include_directories(libstark/src/protocols/common)
include_directories(libstark/src/protocols/common/CryptoCommitment)
include_directories(libstark/src/protocols/Fri)
include_directories(libstark/src/protocols/Fri/common)
include_directories(libstark/src/protocols/Fri/verifier_details)
include_directories(libstark/src/reductions/BairToAcsp)
include_directories(libstark/src/reductions/BairToAcsp/Details)
include_directories(libstark/src/reductions/BairToAcsp/Routing)
include_directories(libstark-tests)
include_directories(libstark-tests/lightCircLib)
include_directories(prevstarkdpm)
include_directories(starkdpm)
include_directories(tinyram/gadgetlib/gadgetlib)
include_directories(tinyram/gadgetlib/gadgetlib/SHA)
include_directories(tinyram/stark-tinyram/src/TinyRAM)
include_directories(tinyram/stark-tinyram/src/TinyRAMtoBair/ConstraintSystemToBair)
include_directories(tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem)

add_library(FFT
        algebra/FFT/src/Basis.cpp
        algebra/FFT/src/Basis.h
        algebra/FFT/src/Definitions.cpp
        algebra/FFT/src/Definitions.h
        algebra/FFT/src/Element.cpp
        algebra/FFT/src/Element.h
        algebra/FFT/src/FFT.cpp
        algebra/FFT/src/FFT.h
        algebra/FFT/src/Polynomials.cpp
        algebra/FFT/src/Polynomials.h
        )

add_library(libstark
        libstark/src/common/Algebra/FieldElementPredicate.hpp
        libstark/src/common/Algebra/FiniteSetInterface.hpp
        libstark/src/common/Algebra/LinearSpace.cpp
        libstark/src/common/Algebra/LinearSpace.hpp
        libstark/src/common/Algebra/MultiVarPoly.cpp
        libstark/src/common/Algebra/MultiVarPoly.hpp
        libstark/src/common/Algebra/MultiVarPolyIddo.hpp
        libstark/src/common/Algebra/ShiftedSubspacePolynomial.cpp
        libstark/src/common/Algebra/ShiftedSubspacePolynomial.hpp
        libstark/src/common/Infrastructure/Infrastructure.cpp
        libstark/src/common/Infrastructure/Infrastructure.hpp
        libstark/src/common/langCommon/Sequence.hpp
        libstark/src/common/Utils/ErrorHandling.cpp
        libstark/src/common/Utils/ErrorHandling.hpp
        libstark/src/common/Utils/specsPrint.cpp
        libstark/src/common/Utils/specsPrint.hpp
        libstark/src/common/Utils/TaskReporting.hpp
        libstark/src/common/Utils/Timing.cpp
        libstark/src/common/Utils/Timing.hpp
        libstark/src/languages/Acsp/AcspInstance.hpp
        libstark/src/languages/Acsp/AcspWitness.hpp
        libstark/src/languages/Acsp/AcspWitnessChecker.cpp
        libstark/src/languages/Acsp/AcspWitnessChecker.hpp
        libstark/src/languages/Acsp/RationalConstraintsSys.hpp
        libstark/src/languages/Bair/BairInstance.hpp
        libstark/src/languages/Bair/BairWitness.hpp
        libstark/src/languages/Bair/BairWitnessChecker.cpp
        libstark/src/languages/Bair/BairWitnessChecker.hpp
        libstark/src/languages/Bair/ConstraintsSys.cpp
        libstark/src/languages/Bair/ConstraintsSys.hpp
        libstark/src/protocols/Ali/common_details/common.cpp
        libstark/src/protocols/Ali/common_details/common.hpp
        libstark/src/protocols/Ali/verifier_details/queriesGen.cpp
        libstark/src/protocols/Ali/verifier_details/queriesGen.hpp
        libstark/src/protocols/Ali/prover.cpp
        libstark/src/protocols/Ali/prover.hpp
        libstark/src/protocols/Ali/verifier.cpp
        libstark/src/protocols/Ali/verifier.hpp
        libstark/src/protocols/common/CryptoCommitment/MerkleCommitment.cpp
        libstark/src/protocols/common/CryptoCommitment/MerkleCommitment.hpp
        libstark/src/protocols/common/proofs.cpp
        libstark/src/protocols/common/proofs.hpp
        libstark/src/protocols/common/queries.hpp
        libstark/src/protocols/common/verifier.cpp
        libstark/src/protocols/common/verifier.hpp
        libstark/src/protocols/Fri/common/common.cpp
        libstark/src/protocols/Fri/common/common.hpp
        libstark/src/protocols/Fri/verifier_details/queryGenerator.cpp
        libstark/src/protocols/Fri/verifier_details/queryGenerator.hpp
        libstark/src/protocols/Fri/prover.cpp
        libstark/src/protocols/Fri/prover.hpp
        libstark/src/protocols/Fri/verifier.cpp
        libstark/src/protocols/Fri/verifier.hpp
        libstark/src/protocols/protocol.cpp
        libstark/src/protocols/protocol.hpp
        libstark/src/reductions/BairToAcsp/Details/AcspRationalSystem.hpp
        libstark/src/reductions/BairToAcsp/Details/AcspSummandsPolynomial.cpp
        libstark/src/reductions/BairToAcsp/Details/AcspSummandsPolynomial.hpp
        libstark/src/reductions/BairToAcsp/Details/boundaryConstraints.hpp
        libstark/src/reductions/BairToAcsp/Details/common.hpp
        libstark/src/reductions/BairToAcsp/Details/commonDeffinitions.cpp
        libstark/src/reductions/BairToAcsp/Details/commonDeffinitions.hpp
        libstark/src/reductions/BairToAcsp/Details/commonInformation.hpp
        libstark/src/reductions/BairToAcsp/Details/commonMappings.cpp
        libstark/src/reductions/BairToAcsp/Details/commonMappings.hpp
        libstark/src/reductions/BairToAcsp/Details/constraints.cpp
        libstark/src/reductions/BairToAcsp/Details/constraints.hpp
        libstark/src/reductions/BairToAcsp/Details/constraintSystemsTestLocations.cpp
        libstark/src/reductions/BairToAcsp/Details/constraintSystemsTestLocations.hpp
        libstark/src/reductions/BairToAcsp/Details/instanceMappings.cpp
        libstark/src/reductions/BairToAcsp/Details/instanceMappings.hpp
        libstark/src/reductions/BairToAcsp/Details/neighborsConstructor.cpp
        libstark/src/reductions/BairToAcsp/Details/neighborsConstructor.hpp
        libstark/src/reductions/BairToAcsp/Details/spaces.cpp
        libstark/src/reductions/BairToAcsp/Details/spaces.hpp
        libstark/src/reductions/BairToAcsp/Details/witnessMappings.cpp
        libstark/src/reductions/BairToAcsp/Details/witnessMappings.hpp
        libstark/src/reductions/BairToAcsp/Details/witnessReduction.cpp
        libstark/src/reductions/BairToAcsp/Details/witnessReduction.hpp
        libstark/src/reductions/BairToAcsp/Routing/BenesNetwork.cpp
        libstark/src/reductions/BairToAcsp/Routing/BenesNetwork.hpp
        libstark/src/reductions/BairToAcsp/Routing/BitReverseButterfliesNetwork.cpp
        libstark/src/reductions/BairToAcsp/Routing/BitReverseButterfliesNetwork.hpp
        libstark/src/reductions/BairToAcsp/Routing/BtrflyBasedPermutation.cpp
        libstark/src/reductions/BairToAcsp/Routing/BtrflyBasedPermutation.hpp
        libstark/src/reductions/BairToAcsp/Routing/DeBruijnPermutationNet.cpp
        libstark/src/reductions/BairToAcsp/Routing/DeBruijnPermutationNet.hpp
        libstark/src/reductions/BairToAcsp/Routing/Deg2PermutationRoutingNet.hpp
        libstark/src/reductions/BairToAcsp/Routing/FoldNetwork.cpp
        libstark/src/reductions/BairToAcsp/Routing/FoldNetwork.hpp
        libstark/src/reductions/BairToAcsp/Routing/LongDeBruijnPermutationNet.cpp
        libstark/src/reductions/BairToAcsp/Routing/LongDeBruijnPermutationNet.hpp
        libstark/src/reductions/BairToAcsp/Routing/LongSymmetricDeBruijnNetwork.cpp
        libstark/src/reductions/BairToAcsp/Routing/LongSymmetricDeBruijnNetwork.hpp
        libstark/src/reductions/BairToAcsp/Routing/MatrixNetwork.hpp
        libstark/src/reductions/BairToAcsp/Routing/PermutationRoutingNet.cpp
        libstark/src/reductions/BairToAcsp/Routing/PermutationRoutingNet.hpp
        libstark/src/reductions/BairToAcsp/Routing/RoutingNetwork.hpp
        libstark/src/reductions/BairToAcsp/Routing/SymmetricDeBruijnNetwork.cpp
        libstark/src/reductions/BairToAcsp/Routing/SymmetricDeBruijnNetwork.hpp
        libstark/src/reductions/BairToAcsp/Routing/TandemNetwork.cpp
        libstark/src/reductions/BairToAcsp/Routing/TandemNetwork.hpp
        libstark/src/reductions/BairToAcsp/BairToAcsp.cpp
        libstark/src/reductions/BairToAcsp/BairToAcsp.hpp
        )

add_library(gadgetlib
        tinyram/gadgetlib/gadgetlib/common_use.cpp
        tinyram/gadgetlib/gadgetlib/common_use.hpp
        tinyram/gadgetlib/gadgetlib/constraint.cpp
        tinyram/gadgetlib/gadgetlib/constraint.hpp
        tinyram/gadgetlib/gadgetlib/gadget.cpp
        tinyram/gadgetlib/gadgetlib/gadget.hpp
        tinyram/gadgetlib/gadgetlib/gadgetMacros.hpp
        tinyram/gadgetlib/gadgetlib/infrastructure.cpp
        tinyram/gadgetlib/gadgetlib/infrastructure.hpp
        tinyram/gadgetlib/gadgetlib/protoboard.cpp
        tinyram/gadgetlib/gadgetlib/protoboard.hpp
        )

#add_executable(gadget-tests
#        tinyram/gadgetlib/gadgetlib/tests/constraint_UTEST.cpp
#        tinyram/gadgetlib/gadgetlib/tests/gadget_UTEST.cpp
#        tinyram/gadgetlib/gadgetlib/tests/gadgetlib2_test.cpp
#        tinyram/gadgetlib/gadgetlib/tests/protoboard_UTEST.cpp
#        tinyram/gadgetlib/gadgetlib/tests/variable_UTEST.cpp
#        )

add_executable(libstark-tests
        libstark-tests/BairToAcsp/AcspSummandsPolynomial_UTEST.cpp
        libstark-tests/BairToAcsp/boundaryConstraints_UTEST.cpp
        libstark-tests/BairToAcsp/constraints_UTEST.cpp
        libstark-tests/BairToAcsp/neighborsConstructor_UTES.cpp
        libstark-tests/BairToAcsp/RoutingNetworks_UTEST.cpp
        libstark-tests/BairToAcsp/witnessReduction_UTEST.cpp
        libstark-tests/lightCircLib/lightCircGate.cpp
        libstark-tests/lightCircLib/lightCircGate.hpp
        libstark-tests/lightCircLib/lightCircPoly.cpp
        libstark-tests/lightCircLib/lightCircPoly.hpp
        libstark-tests/lightCircLib/lightCircPoly_UTEST.cpp
        libstark-tests/lightCircLib/lightCircuit.cpp
        libstark-tests/lightCircLib/lightCircuit.hpp
        libstark-tests/AcspWitnessChecker_UTEST.cpp
        libstark-tests/BairWitnessChecker_UTEST.cpp
        libstark-tests/BairWitnessChecker_UTEST.hpp
        libstark-tests/main.cpp
        libstark-tests/MerkleCommitment_UTEST.cpp
        )

add_library(tinyramlib
        tinyram/stark-tinyram/src/TinyRAM/TinyRAMDefinitions.cpp
        tinyram/stark-tinyram/src/TinyRAM/TinyRAMDefinitions.hpp
        tinyram/stark-tinyram/src/TinyRAM/TinyRAMInstance.cpp
        tinyram/stark-tinyram/src/TinyRAM/TinyRAMInstance.hpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/ConstraintSystemToBair/cs2Bair.cpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/ConstraintSystemToBair/cs2Bair.hpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/ALU.cpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/ALU.hpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/ALUInputConsistency.cpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/ALUInputConsistency.hpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/generalPurpose.cpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/generalPurpose.hpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/MemoryConsraints.cpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/MemoryConsraints.hpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/traceConsistency.cpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/traceConsistency.hpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/transitionFunction.cpp
        tinyram/stark-tinyram/src/TinyRAMtoBair/RamToContraintSystem/transitionFunction.hpp
        )

add_executable(starkdpm
        starkdpm/AES160hashcLOCI.hpp
        starkdpm/AES160hashcLOCI_constraints.cpp
        starkdpm/AES160hashcLOCI_EvalPoly.cpp
        starkdpm/AES160hashcLOCI_GenWitness.cpp
        starkdpm/AES160hashcLOCI_instance.cpp
        starkdpm/AES160hashcLOCI_instance.hpp
        starkdpm/AES160hashcLOCI_witness.cpp
        starkdpm/main.cpp
        )

add_executable(prevstarkdpm
        prevstarkdpm/LOCI_AES160hashchain.hpp
        prevstarkdpm/LOCI_AES160hashchain__GenWitness.cpp
        prevstarkdpm/LOCI_AES160hashchain_constraints.cpp
        prevstarkdpm/LOCI_AES160hashchain_EvalPoly.cpp
        prevstarkdpm/LOCI_AES160hashchain_instance.cpp
        prevstarkdpm/LOCI_AES160hashchain_instance.hpp
        prevstarkdpm/LOCI_AES160hashchain_witness.cpp
        prevstarkdpm/main.cpp
        )

add_executable(stark-tinyram
        tinyram/stark-tinyram/src/main.cpp
        )

add_executable(stark-tinyram-tests
        tinyram/stark-tinyram-tests/ALU_UTEST.cpp
        tinyram/stark-tinyram-tests/ALUInputConsistenctUTEST.cpp
        tinyram/stark-tinyram-tests/ConstraintsSystem2Bair_UTEST.cpp
        tinyram/stark-tinyram-tests/generalPupose_UTEST.cpp
        tinyram/stark-tinyram-tests/main.cpp
        tinyram/stark-tinyram-tests/memory_UTEST.cpp
        tinyram/stark-tinyram-tests/programs_UTEST.cpp
        tinyram/stark-tinyram-tests/traceConsistencyUTEST.cpp
        tinyram/stark-tinyram-tests/transitionFunctionUTEST.cpp)

target_link_libraries(algebralib-tests algebralib)
target_link_libraries(algebralib-tests FFT)
target_link_libraries(algebralib-tests gtest)
target_link_libraries(algebralib-tests gomp)

target_link_libraries(libstark-tests libstark)
target_link_libraries(libstark-tests gadgetlib)
target_link_libraries(libstark-tests algebralib)
target_link_libraries(libstark-tests FFT)
target_link_libraries(libstark-tests gomp)
target_link_libraries(libstark-tests gtest)

target_link_libraries(stark-tinyram-tests tinyramlib)
target_link_libraries(stark-tinyram-tests libstark)
target_link_libraries(stark-tinyram-tests gadgetlib)
target_link_libraries(stark-tinyram-tests algebralib)
target_link_libraries(stark-tinyram-tests FFT)
target_link_libraries(stark-tinyram-tests gomp)
target_link_libraries(stark-tinyram-tests gtest)

target_link_libraries(stark-tinyram tinyramlib)
target_link_libraries(stark-tinyram libstark)
target_link_libraries(stark-tinyram gadgetlib)
target_link_libraries(stark-tinyram algebralib)
target_link_libraries(stark-tinyram FFT)
target_link_libraries(stark-tinyram gomp)

target_link_libraries(prevstarkdpm libstark)
target_link_libraries(prevstarkdpm gadgetlib)
target_link_libraries(prevstarkdpm algebralib)
target_link_libraries(prevstarkdpm FFT)
target_link_libraries(prevstarkdpm gomp)

target_link_libraries(starkdpm libstark)
target_link_libraries(starkdpm gadgetlib)
target_link_libraries(starkdpm algebralib)
target_link_libraries(starkdpm FFT)
target_link_libraries(starkdpm gomp)