# JenkinsExample

A jenkins build automation example, as discussed on [thoughts-on-cpp.com](https://thoughts-on-cpp.com/2019/03/27/introduction-into-build-automation-setup-with-jenkins-and-cmake) for a C++/Qt desktop application utilizing CMake, CTest and CPPCheck.

## Getting Started

This is a very basic build setup defined with jenkins declarative pipeline.
It's using [CMake](https://cmake.org/) for the build process, [CTest](https://cmake.org/cmake/help/v3.14/manual/ctest.1.html) for executing the tests and [CPPCheck](http://cppcheck.sourceforge.net/) for static code analysis


### Prerequisites

- C++11
- [Qt5](https://www.qt.io/) as UI-Framework
- [Catch2](https://github.com/catchorg/Catch2) as Testing-Framework
- [Vcpkg](https://github.com/Microsoft/vcpkg) as Package Manager
- [CPPCheck](http://cppcheck.sourceforge.net/) as Static Code Analyzer
- [Jenkins](https://jenkins.io/) as Build Orchestrator with CMake and CPPCheck plugin

Important to note is that CMake needs the Vcpkg toolchain file to resolve the necessary dependencies
```
-DCMAKE_TOOLCHAIN_FILE={YOUR_PATH_TO_VCPKG}/vcpkg/scripts/buildsystems/vcpkg.cmake
```

## Authors

* **Benjamin Mahr** - [Ben1980](https://github.com/Ben1980)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
