cmake_minimum_required(VERSION 3.15)
project(simExtRML2)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_MACOSX_RPATH 1)

find_package(Boost REQUIRED)

if(NOT LIBPLUGIN_DIR)
    if(DEFINED ENV{COPPELIASIM_ROOT_DIR})
        set(LIBPLUGIN_DIR $ENV{COPPELIASIM_ROOT_DIR}/programming/libPlugin)
    else()
        set(LIBPLUGIN_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../libPlugin)
    endif()
endif()
list(APPEND CMAKE_MODULE_PATH ${LIBPLUGIN_DIR}/cmake)
find_package(CoppeliaSim 4.1.0.0 REQUIRED)

coppeliasim_add_plugin(
    simExtRML2
    LEGACY
    SOURCES
    simExtRML2.cpp
    ReflexxesTypeII/src/TypeIIRML/ReflexxesAPI.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLCalculatePositionalExtrems.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLDecisions.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLDecisionTree1A.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLDecisionTree1B.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLDecisionTree1C.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLDecisionTree2.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLFallBackStrategy.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLIsPhaseSynchronizationPossible.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLPolynomial.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLPosition.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLQuicksort.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLSetupModifiedSelectionVector.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLStep1.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLStep1IntermediateProfiles.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLStep1Profiles.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLStep2.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLStep2IntermediateProfiles.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLStep2PhaseSynchronization.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLStep2Profiles.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLStep2WithoutSynchronization.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLStep3.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLVelocity.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLVelocityCalculatePositionalExtrems.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLVelocityFallBackStrategy.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLVelocityIsPhaseSynchronizationPossible.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLVelocityMethods.cpp
    ReflexxesTypeII/src/TypeIIRML/TypeIIRMLVelocitySetupPhaseSyncSelectionVector.cpp
)
target_include_directories(simExtRML2 PRIVATE ReflexxesTypeII/include)
