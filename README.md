# FastCV

### Introduction
  
FastCV is a proprietary computer vision library developed by Qualcomm, optimized for Snapdragon chipsets. It provides a collection of frequently used computer vision (CV) functions designed to run efficiently on Qualcomm hardware. FastCV supports both generic ARM architecture and Snapdragon-specific implementations, offering hardware acceleration for CV tasks.<br>
FastCV is designed for developers interested in creating sophisticated CV apps, as well as CV middleware developers looking to build the frameworks necessary for everyday developers to include computer vision functionality in their apps.

### Practical Applications
  
FastCV is widely used in applications requiring real-time CV processing, such as:<br>
- Low-light image enhancement: Filters like bilateral, median, and guided filters can enhance images captured in poor lighting conditions.
- Feature detection and tracking: Functions like FAST corner detection and optical flow tracking are optimized for Snapdragon DSPs.
- Image transformations: Operations like resizing, warping, and affine transformations are accelerated for better performance.

### Features supported
  
FastCV provides comprehensive support for a wide range of computer vision and image processing algorithms. The library is designed to enable efficient development and deployment of visionbased applications, offering capabilities across multiple domains, including:<br>
- **Color space conversions** to support various image formats and visual representations.
- **Feature detection and extraction** for identifying key points and patterns within images.
- **Image transformations**, such as resizing, filtering, and geometric operations.
- **Object detection** to identify and locate objects within images.
- **Mathematical and vector operations** optimized for highperformance computation.
- **Clustering and search algorithms** to support similarity matching and data organization.
For more detailed list of features and API use, please refer to this [doc](https://docs.qualcomm.com/doc/80-79511-2/topic/overview.html).

### Workflow Overview
  
The execution flow for leveraging FastCV within an application is structured as follows:<br>
- The user application initiates a call to the the appropriate FastCV API, passing the desired parameters.
- The FastCV API then interfaces with the FastCV library available on the target device to carry out the requested CV operation.
- Depending on the input parameters and execution configuration, the computation is offloaded to either the CPU or the DSP for optimized performance.
- For DSP offloading, we have a dependency on **Fastrpc Debian package**.

### Building
  
The qcom-fastcv-binaries.spec file extracts prebuilt binaries from the tarball and installs them into the appropriate package staging directories.

### Installation
- Make sure to install [Fastrpc RPM package](https://src.fedoraproject.org/rpms/fastrpc) otherwise FastCV RPM package will give dependency errors.
- Install the package using command: `sudo dnf install libfastcvopt1-1.8.9-1.el10.aarch64.rpm`
- Once installation is complete one should see `libfastcvopt.so.1` in `/usr/lib/`.

### Testing
  
For testing purposes, the package comes with a sample test app: fastcv_simple_test64. By default, it will be installed in /usr/bin. To run it use below commands:<br>
- `adb shell`
- `chmod 777 /usr/bin/fastcv_simple_test64`
- `exit`
- `adb shell /usr/bin/fastcv_simple_test64`

### Bug Reporting Guidelines
  
When reporting bugs, please provide the following details to facilitate debugging:<br>
- **Platform/SoC Name:** Specify the name of the platform or System on Chip (SoC) being used.
- **User Space Library Version/HLOS Build Details:** Include the version of the user space library and details of the High-Level Operating System (HLOS) build.
- **stdout & stderr for User Space:** Share the standard output and standard error logs for the user space.
- **User Library Logs:** Can be captured from `/var/log/syslog`.
- **QXDM Logs:** Provide QXDM logs for DSP failures.
- **Tests Run & Parameters:** Detail the tests that were run along with their parameters, including any environment variables explicitly set for FastCV, API used and any custom parameters given.
- **Custom Test Code:** If a custom test was conducted, please share a code snippet or the complete code to reproduce the issue.

### License
  
pkg-rpm-qcom-fastcv-binaries is licensed under the [BSD-3-Clause License](https://spdx.org/licenses/BSD-3-Clause.html). See [LICENSE.txt](https://github.com/qualcomm-linux/pkg-qcom-sensors/blob/qcom/debian/trixie/LICENSE.txt) for the full license text.