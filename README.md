# rocminfo
ROCm Application for Reporting System Info

## To Build
Use the standard cmake build procedure to build rocminfo. The location of ROCM
root (parent directory containing ROCM headers and libraries) must be provided
as a cmake argument using the standard CMAKE_PREFIX_PATH cmake variable. Building
the package also requires the rocm-cmake helper files.

For example, building from the CMakeLists.txt directory
might look like this:

mkdir -p build

cd build

cmake -DCMAKE_PREFIX_PATH=/opt/rocm ..

make

cd ..


Upon a successful build the binary, rocminfo, and the python script, rocm_agent_enumerator, will be in the build folder.

## Execution

"rocminfo" gives information about the HSA system attributes and agents.

"rocm_agent_enumerator" prints the list of available AMD GCN ISA. There exist four different ways how it is generated:

1. ROCM_TARGET_LST : a user defined environment variable, set to the path and filename where to find the "target.lst" file. This can be used in an install environment with sandbox, where execution of "rocminfo" is not possible.

2. target.lst : user-supplied text file, in the same folder as "rocm_agent_enumerator". This is used in a container setting where ROCm stack may usually not available.

3. rocminfo : a tool shipped with this script to enumerate GPU agents available on a working ROCm stack.

4. lspci : enumerate PCI bus and locate supported devices from a hard-coded lookup table.

