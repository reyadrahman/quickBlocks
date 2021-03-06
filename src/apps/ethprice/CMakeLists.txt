# minimum cmake version supported
cmake_minimum_required (VERSION 2.6)

# application project
project (ethprice)

# The sources to be used
file(GLOB SOURCE_FILES "*.cpp")

# Output
set(EXECUTABLE_OUTPUT_PATH "${CMAKE_SOURCE_DIR}/../bin")

# Define the executable to be generated
set(TOOL_NAME "ethprice")
add_executable(${TOOL_NAME} ${SOURCE_FILES})

# Add the project static libs at linking
target_link_libraries (${TOOL_NAME} wallet token ${BASE_LIBS})

# Testing
# Define paths to test folder and gold folder
set(TEST_EXE "${EXECUTABLE_OUTPUT_PATH}/${TOOL_NAME}")
set(PROJ_NAME "apps")
set(TEST_PATH "${TEST_PATH}/${PROJ_NAME}/${TOOL_NAME}")
set(GOLD_PATH "${GOLD_PATH}/${PROJ_NAME}/${TOOL_NAME}")

# Additional target to make the README.md
build_readme(${CMAKE_CURRENT_SOURCE_DIR} ${TOOL_NAME})

# Function to run an individual test case
function(run_test testName)
     run_the_test(${TEST_PATH} ${GOLD_PATH} ${testName} ${TEST_EXE} ${ARGN})
endfunction(run_test)

# Enter one line for each individual test
run_test("ethprice_README"          "-th")
run_test("ethprice_no_params"            )
run_test("ethprice_invalid_param_1" "-x" )
run_test("ethprice_at_invalid"      "-a")
run_test("ethprice_at_00"           "-a:1438272138")
run_test("ethprice_period_invalid"  "-p")
run_test("ethprice_period_00"       "-p:60")
run_test("ethprice_period_01"       "--period:240")
run_test("ethprice_period_02"       "--period:12")
run_test("ethprice_when_invalid"    "-w")
run_test("ethprice_when_00"         "-w:14")
run_test("ethprice_when_01"         "--when:19")
run_test("ethprice_verbose_00"      "-v")
run_test("ethprice_verbose_01"      "-v:1")

# THESE TESTS PROBABLY WORK, BUT THEY TAKE VERY LONG
#run_test("ethprice_clear" -c")
#run_test("ethprice_freshen_00" "--freshen")
#run_test("ethprice_invalid_param_2" "-" )
#run_test("ethprice_freshen_invalid" "-f")
