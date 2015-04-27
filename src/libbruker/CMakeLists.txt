find_package(FLEX REQUIRED)

FLEX_TARGET(BrukerScanner brukerlex.l ${CMAKE_CURRENT_BINARY_DIR}/brukerlex.cpp)


add_definitions(-fPIC)

add_library(
    bruker
    SHARED
    brukerparameterparser.cpp
    brukerrawdata.cpp
    ndarray.cpp
    ${FLEX_BrukerScanner_OUTPUTS}
)

include_directories(
  ${Boost_INCLUDE_DIR}	
  ${CMAKE_CURRENT_SOURCE_DIR}
  ${CMAKE_CURRENT_SOURCE_DIR}/libbruker
  )

install(TARGETS bruker DESTINATION lib)

