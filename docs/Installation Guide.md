# Installation Guide

- [Installation Guide](#installation-guide)
  - [1. Prerequisites](#1-prerequisites)
  - [2. Sionna Installation via Pip](#2-sionna-installation-via-pip)

## 1. Prerequisites
1. Install [Python](https://www.python.org/downloads/) (This tutorial uses Python v3.12.4).
2. On the project folder, create Python Virtual Environment:
   1. Create venv:
        ```bash
        python -m venv venv
        ```
    2. Activate venv, then your terminal should shown `(venv)` later:
        - Windows:
            ```bash
            venv\Scripts\activate
            ```
3. Install LLVM:
   1. Visit the LLVM GitHub releases page: LLVM GitHub Releases
   2. Look for the latest release. It should be at the top of the list.
   3. Under the release, look for the "Assets" section and find the Windows pre-built binary. It should be a .exFe file named something like LLVM-<version>-win64.exe.
   4. Click on the .exe file to download it.
   5. Run the downloaded .exe file and follow the instructions to install LLVM.
   6. Check the installation result:
        ```bash
        clang --version
        ```
        **Output**:
        ```console
        clang version 18.1.7
        Target: x86_64-pc-windows-msvc
        Thread model: posix
        InstalledDir: C:\Program Files\LLVM\bin
        ```

## 2. Sionna Installation via Pip
1. Install Sionna-RT package:
    ```bash
    pip install sionna
    ```
2. To run the Ray Tracer on CPU, LLVM is required by DrJit. You can upgrade to the latest version via:
    ```bash
    pip install --upgrade ipykernel jupyterlab
    ```
3. Test the insallation in Python:
    ```bash
    python
    ```

    ```python
    import sionna
    print(sionna.__version__)
    ```

    **Output**:
    ```bash
    0.15.1
    ```
