# 🌫️ BlackFog Framework

**BlackFog** is a modular framework designed to explore the depths of Windows internals and test the limits of modern EDR (Endpoint Detection and Response) systems. 

This project is a hybrid beast: combining the raw power of **low-level C++** with the flexibility of **C#**, compiled via **NativeAOT** to run as a standalone, stealthy native binary.

---

## 🏗️ Architecture

### 1. `haze` (The Muscle / C++)
The Stage 0 loader responsible for "turning off the lights" and preparing the environment.
* **Indirect Syscalls**: Bypasses EDR hooks by talking directly to the kernel using custom Assembly wrappers.
* **Defense Evasion**: Patches `amsi.dll` and `ntdll.dll`  in memory to blind system monitoring.
* **Build Optimization**: 
    - **Minimized Footprint**: Compiled with size optimization flags to reduce binary weight.
    - **Disabled Mitigations**: Security checks like `/GS` and `/guard:cf` are disabled to allow for low-level patching and custom execution flow.

### 2. `BlackFogCore` (The Brain / C# NativeAOT)
The Stage 1 logic module, written in C# but transformed into a native DLL.
* **Dependency-Free**: Thanks to NativeAOT, it doesn't require .NET to be installed.
* **Stealth Bridge**: Receives syscall addresses directly from the loader to perform memory operations without triggering API monitors.

---

## 🛠️ Features
- [x] **NativeAOT Integration**: C# code running as a fully native, unmanaged DLL.
- [x] **Indirect Syscalls**: Manual invocation of `Nt` functions to evade user-mode hooking.
- [x] **Defense Evasion**: Dynamic memory patching for AMSI.
- [x] **Network Recon**: Built-in discovery module for horizontal movement research.

---


<img width="638" height="280" alt="image" src="https://github.com/user-attachments/assets/f23d44ea-08ef-41ad-893c-57c65e600a1e" />


## 💻 Tech Stack
* **C++**: Low-level orchestration and memory manipulation.
* **C# (NativeAOT)**: High-level logic and network modules.
* **Assembly (x64)**: Direct syscall implementation.

---

## ⚠️ Disclaimer
This project is created strictly for educational purposes and security research. The goal is to understand Windows internals and improve defensive strategies. The author is not responsible for any misuse of this code.
