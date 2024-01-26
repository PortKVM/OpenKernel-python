# OpenKernel

OpenKernel is a Python implementation of a Linux Kernel.

## Features

* Process management
* Device management
* Interrupt handling
* System calls
* make your own Linux!

## Installation

To install OpenKernel, run the following command:
`pip install OpenKernel`

## Usage

```python
from OpenKernel import Kernel, Process, Program, Instruction

# Create a new kernel.
kernel = Kernel()

# Create a new process.
process = Process(1, 0, Program([
    Instruction("mov", "r0", "1"),
    Instruction("mov", "r1", "2"),
    Instruction("add", "r2", "r0"),
    Instruction("mov", "r0", "r2"),
    Instruction("hlt")
]))

# Add the process to the kernel.
kernel.add_process(process)

# Start the kernel.
kernel.start()
```

They can then use OpenKernel to create their own operating systems.
Here is an example of how a developer could use OpenKernel to create a clone of Debian!:

```python
from OpenKernel import Kernel, Process, Program, Instruction

# Create a new kernel.
kernel = Kernel()

# Create a new process for the init system.
init_process = Process(1, 0, Program([
    # Mount the root filesystem.
    Instruction("mount", "/dev/sda1", "/"),

    # Start the system services.
    Instruction("start", "sshd"),
    Instruction("start", "httpd"),

    # Run the shell.
    Instruction("run", "/bin/bash")
]))

# Add the init process to the kernel.
kernel.add_process(init_process)

# Create a new process for each user.
for user in get_users():
    user_process = Process(user.uid, 0, Program([
        # Create the user's home directory.
        Instruction("mkdir", "/home/" + user.username),

        # Change to the user's home directory.
        Instruction("cd", "/home/" + user.username),

        # Run the user's shell.
        Instruction("run", "/bin/bash")
    ]))

    # Add the user process to the kernel.
    kernel.add_process(user_process)

# Start the kernel.
kernel.start()
```

### Debian Bin Files will be uploaded to Lilyhosting and Google drive soon, So you could get your own linux!

## PortKVM Authors
- Katy (Owner & Creator of the Linux Openkernel)
- Ki77y666 (A Member & in weekends)
