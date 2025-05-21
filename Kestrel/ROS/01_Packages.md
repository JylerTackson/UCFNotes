A **Package** within ROS 2 is an organizational unit for the ROS 2 code. Using a custom Package we can configure our code such that we can:
- Install the code from anywhere using the package
- Share the code with any members by using the package

You can create a package using either **CMake or Python**, we will use CMake:
## CMake Package:
- - `CMakeLists.txt` file that describes how to build the code within the package
- `include/<package_name>` directory containing the public headers for the package
- `package.xml` file containing meta information about the package
- `src` directory containing the source code for the package
```
my_package/
     CMakeLists.txt
     include/my_package/
     package.xml
     src/
```

### Packages x Workspace:
A single workspace will house as many packages as are needed
**NOTE:** You are unable to nest packages.


# Create a Package:
