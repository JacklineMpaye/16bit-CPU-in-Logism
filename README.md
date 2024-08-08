# 16bit-CPU-in-Logism
This is a 16-bit processor (CPU) built using logism evolution
# 1. Introduction
This documentation provides a comprehensive overview of the design, simulation, and implementation of a 16-bit CPU using Logisim Evolution. We aimed to build a functional 16-bit CPU that can execute basic instructions, including load, store, arithmetic, and control operations from our experience from Comput. The CPU design is modular, and scalable, and can be expanded with additional instructions and features in the future.
# 2. Design Overview
The CPU design is based on a simplified architecture that includes the following key components:
 Program Counter (PC): Keeps track of the current instruction address.
Instruction Register (IR): Holds the currently executing instruction.
Arithmetic Logic Unit (ALU): Performs arithmetic and logical operations.
Registers: Small, fast storage locations for temporary data.
Control Unit: Directs the operation of the CPU, decoding instructions, and generating control signals.
Memory: Stores instructions and data.
# 3. Components and Modules
# 3.1 Program Counter (PC)
The PC is a 16-bit register that increments after each instruction fetch, pointing to the next instruction to be executed.
# 3.2 Instruction Register (IR)
The IR holds the instruction currently being executed. It fetches instructions from memory based on the address provided by the PC.
# 3.3 Arithmetic Logic Unit (ALU)
The ALU performs arithmetic (addition, subtraction) and logical operations (AND, OR, NOT). It takes input from the registers and provides the result back to the registers or memory.
# 3.4 Registers
We implemented two general-purpose registers one 8-bit ($s0 to $s7) and one 16-bit wide register for temporary data storage. 
# 3.5 Control Unit
The control unit decodes the instruction in the IR and generates control signals to orchestrate the CPU's operation. It manages data flow between the ALU, registers, and memory.
# 3.6 Memory
The memory module is divided into instruction memory and data memory. Instructions are stored in the first 8 addresses, while data is stored in the last 8 addresses.
# 4. Instruction Set Architecture (ISA)
The CPU supports the following instructions, each represented by an 8-bit opcode and an 8-bit operand:
LoadA: 00000000 (Load content from memory to register A)
LoadB: 00000001 (Load content from memory to register B)
Arithmetic: 00000010 (Perform arithmetic operation on registers A and B)
Store: 00000011 (Store result from register A to memory)
# 5. Design and Simulation Process
# 5.1 Initial Design
We designed each component as a separate module in Logisim. And built up a high-level block diagram of the CPU, identifying the key components and their interconnections by interfacing the individual components.
# 5.2 Component Implementation
We implemented and tested each component individually:
Program Counter: A 16-bit register with increment functionality.
Instruction Register: A 16-bit register to hold the current instruction.
ALU: Capable of performing addition, subtraction, AND, OR, and NOT operations.
Registers: Implemented as a register files with read and write capabilities. The 8 bit register was used for Memory address and the 16bit register was used for making the Register A, register B, output register, memory buffer register.
Control Unit: A finite state machine to generate control signals based on the opcode.
# 5.3 Integration
After testing individual components, we integrated them into a complete CPU design. We connected the components according to the block diagram, ensuring data paths and control signals were correctly routed.
# 5.4 Simulation
We simulated the CPU by loading a set of test instructions into memory and observing the execution cycle. We used Logisim's simulation features to step through each clock cycle and verify the CPU's behavior.
# 6. Challenges Faced
# 6.1 Synchronization Issues
One of the initial challenges was ensuring all components were properly synchronized with the clock signal and that they were all connected properly without any blockages between the instructions flow due to crossing of lines. We faced issues with data being latched correctly, especially in the registers and memory.
Solution: We resolved this by carefully disintegrating and re-designing the components with their connections and the clock and ensuring that all components received the clock signal simultaneously.
# 6.2 Ambiguity of the Project
Designing the CPU required a lot of steps and a lot of components like ALU, registers, counters etc were required to be built and integrated. An error in one of them caused the CPU not to work as required.
Solution: We redesigned each of the components following the instructions seamlessly and tested each of the components to ensure that each worked before interfacing it with the CPU.
# 7. Insights and Learnings
# 7.1 Modular Design
Designing the CPU in a modular fashion made it easier to test and debug individual components. This approach also allows for future expansions and modifications.
# 7.2 Importance of Simulation
Simulation was crucial for verifying the functionality of the CPU. It allowed us to identify where the red and oranges lines were caused from and fix issues early in the design process, saving time and effort.
# 7.3 Understanding Control Flow
Implementing the control unit provided valuable insights into how CPUs manage instruction execution and data flow. We gained a deeper understanding of finite state machines and their role in control logic.
# 8. Conclusion
The design and implementation of a 16-bit CPU in Logisim Evolution was a challenging yet rewarding project. We successfully built a functional CPU capable of executing a basic set of instructions. This process enhanced our understanding of digital logic design, CPU architecture, and simulation techniques. The modular design ensures that the CPU can be expanded and improved in future iterations.


