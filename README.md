# Distributed-Edge-AI-Implementation-and-Documentation
This project successfully designed, configured, and implemented a functional four-node compute cluster utilizing StarFive RISC-V single-board computers. The work covered all layers of the stack, from physical networking and OS imaging to establishing a modern, RISC-V-native software development toolchain. A key achievement was establishing robust, SSH-less communication between all nodes and creating a custom, recoverable OS image for reliable deployment. This cluster is now fully prepared for distributed computing and parallel processing research.

The cluster is built on the RISC-V (Reduced Instruction Set Computer - Five) architecture, positioning the project at the forefront of open hardware design.
Cluster Size: Four (4) distinct computing nodes.
Operating System: Debian GNU/Linux 13 (trixie) was selected for its stability and strong support for the RISC-V architecture.
Establishing a reliable network was the most critical initial step. The goal was to ensure high-speed, secure, and uninterrupted internode communication.
Topology & Configuration: The network configuration included meticulous IP addressing and subnet configuration across all four nodes. Significant effort was dedicated to troubleshooting and resolving complex routing issues to guarantee every node could communicate efficiently with all others.
Security & Automation: SSH-less communication was implemented across the cluster. This is essential for automation scripts and distributed workload managers, as it allows nodes to execute commands on peers without manual password entry, relying instead on key-based authentication.
To ensure cluster consistency and recoverability, a structured approach to storage preparation was employed:
Card Partitioning: The cluster's storage cards were carefully partitioned to separate the boot, kernel, and root filesystem components, ensuring a stable boot process.
Image Creation and Recovery: A master customized OS image was created after the complete software stack and network configurations were finalized. This single image serves as the gold standard for all nodes, allowing for rapid deployment (flashing) and a clear card recovery procedure to minimize downtime and guarantee all nodes are always identical.

The established software environment provides a complete, modern toolchain, natively compiled for the riscv64-unknown-linux-gnu target, enabling advanced development and compilation on the cluster itself.
Tool
Version/Details
Role in the Cluster Development Environment
gcc
Version 13
The primary and latest version of the GNU Compiler Collection, used for compiling performance-critical C/C++ applications.
clang
Debian version 19.1.7
The LLVM compiler front-end, offering modern compilation and optimization features alongside GCC.
lld
Debian LLD 19.1.7
A fast, modern linker from the LLVM project, significantly speeding up the final linking phase of large projects.
cmake
Version 3.31.6
The meta-build system for defining how source code is compiled, ensuring cross-platform and cross-architecture build consistency.
ninja-build
Version 1.12.1
A small build system focused on speed, typically used as the backend for CMake to execute builds in parallel.
python
Version 3.11
The scripting engine used for automation, cluster monitoring, and running high-level scientific libraries.
Repository
deb http://deb.debian.org/debian/ trixie main contrib non-free non-free-firmware
Confirms access to the official Debian trixie repositories, including non-free components often required for firmware.
