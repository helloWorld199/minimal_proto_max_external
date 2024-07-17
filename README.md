Simple max external with a protobuf dependency which gives Error 193 on M4L.

## Dependencies

1. **Install Protobuf**
   - Protobuf has been installed using vcpkg.
   - Current Protobuf version: `25.1.0`.

2. **Install min-api**
   - Use this specific version of the min-api: [min-api @ 4ba9c1b2adb53eab4d9896f0c5005208452d1577](https://github.com/Cycling74/min-api/tree/4ba9c1b2adb53eab4d9896f0c5005208452d1577).

3. **Modify CMakeLists.txt**
   - Modify the `CMakeLists.txt` file accordingly to detect min_api, at line 8.

## Installation & Compilation Instructions

1. **Run getlibs.py**
   - Execute `getlibs.py` to generate a text file with all the libraries that need to be linked to the final external. It basically scans the whole vcpkg/lib folder. You should get something like lib_files_list.txt.

2. **Run CMake**
   - From the main folder, run the following command:
     ```sh
     cmake -G "Visual Studio 17 2022" -S . -B solution --preset debug
     ```

3. **Build the Visual Studio Solution**
   - Open the generated Visual Studio solution.
   - Build the solution using the `/MTd` flag for Runtime Library and static linking to avoid manually configuring Max to find the DLLs.
