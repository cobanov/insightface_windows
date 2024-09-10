# InsightFace Windows Installation Guide

This guide will walk you through the installation of the InsightFace package on a Windows environment, including the necessary dependencies and configurations.

## TL;DR

```bash
python -m venv venv
venv\Scripts\activate
pip install "numpy<2"
pip install whls\insightface-0.7.3-cp310-cp310-win_amd64.whl onnx==1.16.1 onnxruntime-gpu==1.19.2
```

## Prerequisites

- **Python**: Make sure you have Python 3.9 or higher installed on your system.
- **Desktop Development with C++**: This can be installed via Visual Studio Installer to ensure compatibility with the necessary packages.
- **Microsoft Visual C++ Redistributable**: Download and install the Microsoft Visual C++ Redistributable from the link below:
  - [Microsoft Visual C++ Redistributable (x64)](https://aka.ms/vs/17/release/vc_redist.x64.exe)

### Step-by-Step Installation

1. **Install Desktop Development with C++**

   - Open **Visual Studio Installer**.
   - Install the **Desktop Development with C++** workload to ensure compatibility with the required C++ components for packages like ONNX and InsightFace.

2. **Set up a Python Virtual Environment**

   Open a terminal or command prompt and navigate to your project directory. Then run the following commands to create and activate a virtual environment:

   ```bash
   python -m venv venv
   venv\Scripts\activate
   ```

   This creates a virtual environment named `venv` and activates it.

3. **Install Required Packages**

   1. **Install NumPy version compatible with ONNX (NumPy 1.x)**:

      InsightFace and ONNX currently require NumPy 1.x for compatibility. You can install it with the following command:

      ```bash
      pip install "numpy<2"
      ```

   2. **Install InsightFace, ONNX, and ONNXRuntime-GPU**:

      - Download the necessary `.whl` files for InsightFace and the specific version of ONNX/ONNXRuntime-GPU from a trusted source.
      - Navigate to the folder containing your `.whl` files or update the path as needed.

      Install them using the following command:

      ```bash
      pip install -m whls/insightface_<your_version>.whl onnx==1.16.1 onnxruntime-gpu==1.19.2
      ```

4. **Verify the Installation**

   After the installation is complete, verify that the packages have been installed successfully by running the following command in the Python REPL:

   ```python
   >>> import insightface
   >>> import onnx
   >>> import onnxruntime
   ```

   If no errors are encountered, the installation was successful.

### Troubleshooting

- **DLL Load Failure**: If you encounter any errors related to DLL loading or missing files, ensure that the Microsoft Visual C++ Redistributable is installed and that your system’s PATH includes the correct Python and library directories.
- **NumPy Compatibility Issues**: If there are issues related to NumPy, ensure that you have downgraded to `numpy<2`.

### Optional: CPU-only Version of ONNXRuntime

If you do not have a GPU or prefer to run ONNX on the CPU, you can install the CPU-only version of `onnxruntime` instead of the GPU version:

```bash
pip uninstall onnxruntime-gpu
pip install onnxruntime
```

### Additional Resources

- [InsightFace Documentation](https://github.com/deepinsight/insightface)
- [ONNX Documentation](https://onnx.ai/)
