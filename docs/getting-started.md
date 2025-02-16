---
hide:
  - toc
---

# Getting Started

## Course Modules

Use the table below to find a course module. If you are not sure whether you have all the needed background knowledge, start with [Complex Numbers](./background-math/complex-numbers.md). To jump right into quantum computing fundamentals, go to [Qubits](./quantum-concepts/qubits.md).

| Background Math | Classical Computing | Qubits and Quantum Gates | Multi-Qubit Systems | Quantum Circuits | Quantum Protocols | Quantum Algorithms | Quantum Error Correction | Execution on Quantum Computers | 
| - | - | - | - | - | - | - | - | - |
| [Complex Numbers](./background-math/complex-numbers.md) | [Digital Information](./classical-computing/digital-information.md) | [Qubits](./quantum-concepts/qubits.md) | [Qubit Registers](./quantum-concepts/qubit-registers.md) | [Complex Superpositions](./quantum-concepts/complex-superpositions.md) | [Quantum Interference](./quantum-concepts/quantum-interference.md) | [Deutsch-Jozsa Algorithm](./quantum-algorithms/deutsch-jozsa-algorithm.md) | [Bit-Flip Error Correction](./error-correction-codes/bit-flip-error-correction.md) | [Intro to Qiskit](./software-tools/intro-qiskit.md) |
| [Vectors](./background-math/vectors.md) | [Endianness](./classical-computing/endianness.md) | [The Bloch Sphere](./quantum-concepts/bloch-sphere.md) | [Multi-Qubit Gates](./quantum-concepts/multi-qubit-gates.md) | [Quantum Circuit Diagrams](./quantum-concepts/quantum-circuit-diagrams.md) | [Superdense Coding](./quantum-algorithms/superdense-coding.md) | [Grover's Algorithm](./quantum-algorithms/grovers-algorithm.md) | [Steane ECC](./error-correction-codes/steane-ecc.md) | [Cloud-Based Machines](./real-execution/cloud-based-machines.md) |
| [Matrices](./background-math/matrices.md) | [Digital Logic](./classical-computing/digital-logic.md) | [Single-Qubit Gates](./quantum-concepts/single-qubit-gates.md) | [Nonlocal Games](./quantum-concepts/nonlocal-games.md)| [The Quirk Tool](./software-tools/quirk-tool.md) |  | [Simon's Algorithm](./quantum-algorithms/simons-algorithm.md) | | [Resource Estimation and Practicality Assessment](./real-execution/resource-estimation.md) | 
| [Bra-ket and Tensor Notation](./background-math/braket-tensor-notation.md) | [Low-level Programming](./software-development/low-level-programming.md) | [Intro to Q#](./software-tools/intro-qsharp.md) |  | |  | [Quantum Fourier Transform](./quantum-algorithms/qft.md) |  | [Closing Thoughts and Next Steps](./real-execution/whats-next.md) |
| | [High-level Programming](./software-development/high-level-programming.md) | [Lab Tutorial: Single-Qubit Gates](./labs/lab1.md) |  | |  | [Shor's Algorithm](./quantum-algorithms/shors-algorithm.md) |  |
| | [Visual Studio](./software-development/visual-studio.md) | | | | |  |
| | [Visual Studio Code](./software-development/visual-studio-code.md) | | | | |  |

## Lab Exercises

[Download :material-download:](./exercises.zip){: .md-button .md-button--primary }

Click the button above to download the lab exercises and extract the contents of the .zip file

## Installation

### Visual Studio

- Install [Visual Studio Community](https://visualstudio.microsoft.com/vs/community/) with the .NET Core cross-platform development workload enabled

- Install the [Microsoft Quantum Development Kit extension](https://marketplace.visualstudio.com/items?itemName=quantum.DevKit) for Visual Studio

- Open `Intro to Quantum Software Development.sln` in Visual Studio

### Visual Studio Code

- Using Windows 10 or 11:
    - Download [.NET 6.0 SDK for Windows (x64)](https://wingetgui.com/apps?id=Microsoft.DotNet.SDK.6&v=6.0.300).
    - Download [VS Code](https://code.visualstudio.com/download) for Windows
    - Use the extension browser in VS Code on the left
        - Install the Quantum Development Kit extension for VS Code
        - Install the C# extension
        - Install the .NET Core Test Explorer extension

- Using Windows 10 or 11 + Windows Subsystem for Linux (advanced):
    - Install Linux on windows with [WSL](https://docs.microsoft.com/en-us/windows/wsl/install) 
    - Download Ubuntu for Windows (20.04 LTS should work best) from the Microsoft Store
    -  Open Ubuntu, create profile, and paste the following into the terminal: 
    ```wget https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
    sudo dpkg -i packages-microsoft-prod.deb
    rm packages-microsoft-prod.deb
    ```

    and then this:
    
    ```
    sudo apt-get update; \
    sudo apt-get install -y apt-transport-https && \
    sudo apt-get update && \
    sudo apt-get install -y dotnet-sdk-6.0=6.0.300-1
    ```
    - Download [VS Code](https://code.visualstudio.com/download) for Windows (NOT Linux!!):
    - Install the Remote Development Kit extension for VS Code from the extension browser on the left
    - On the bottom left, a new green icon should be visible. Click this, then select Remote-WSL: New Window to open your Linux terminal in VS Code.
    - Now that VS Code is using your Ubuntu terminal, install all other extensions on the 'WSL' version of your VS Code.
        - Install the Quantum Development Kit extension
        - Install the C# extension
        - Install the .NET Core Test Explorer extension

- Using MacOS with x64 chip:
    - Make sure the relevant terminal packages are updated with the following commands:
        - `sudo softwareupdate -i -a`
        - `xcode-select --install`
    - Download [].NET 6.0 SDK](https://dotnet.microsoft.com/en-us/download) for macOS (x64)
    - Download [VS Code](https://code.visualstudio.com/download) for macOS
    - Use the extension browser in VS Code on the left:
        - Install the Quantum Development Kit extension
        - Install the C# extension
        - Install the .NET Core Test Explorer extension

- Using any OS with a Docker container:
    - Install [Docker Desktop](https://www.docker.com/products/docker-desktop/) for Windows/Mac
    - If you are using WSL 2 on Windows, to ensure the WSL 2 back-end is enabled: Right-click on the Docker taskbar item and select Settings. Check Use the WSL 2 based engine and verify your distribution is enabled under Resources > WSL Integration.
    - When not using the WSL 2 back-end, right-click on the Docker task bar item, select Settings and update Resources > File Sharing with any locations your source code is kept. See tips and tricks for troubleshooting.
    - Download [VS Code](https://code.visualstudio.com/download) for your OS:
    - Install the Remote Development Kit extension for VS Code from the extension browser on the left
    - On the bottom left, a new green icon should be visible. Click this, then select 'Open Folder in Container' to open VS Code in a development container that will use Ubuntu and has dotnet already installed.
    - Now that VS Code is using your container, install all other extensions on the container version of VS Code, unless recommended otherwise.
        - Install the Quantum Development Kit extension
        - Install the C# extension
        - Install the .NET Core Test Explorer extension

To create and run a new Q# project in VS Code, follow the steps [here](https://docs.microsoft.com/en-us/azure/quantum/how-to-command-line-local?tabs=tabid-vscode). Linked here are more detailed use instructions for [Visual Studio](software-development/visual-studio.md) and [Visual Studio Code](software-development/visual-studio-code.md).

## Use

Each exercise consists of functions or operations that have not been implemented. The project includes unit tests that validate whether the implementation is correct. Use the [Test Explorer](https://docs.microsoft.com/en-us/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019) to see which exercises have been completed successfully. The first time you open the solution, pull up the Test Explorer pane using the toolbar option `Test` > `Test Explorer`, and then click the green `Run All Tests In View` button. After that, you can expand the tree and run tests individually. You can see the output of a selected test by clicking the `Open additional output for this result` link.

See the [Visual Studio](/software-development/visual-studio) module for info on debugging.
