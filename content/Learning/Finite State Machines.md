A finite state machine is a model that is used to represent the behavior of systems that can be in exactly one of a finite number of states at a given time. As an electrical engineer, I apply finite state machines to digital logic design, specifically sequential logic, where the concept of memory implies that there are many states that the system can possibly exist in.

In digital design, a sequential logic system is composed of four parts:
1. Inputs
2. Next State Logic - encoder that uses combinational logic to determine the next state values.
3. State Memory - sequential logic stored in memory devices such as flip-flops to determine the current state.
4. Output Logic - Combinational logic to determine the output.

This structure can be described in two ways: a Mealy state machine, where outputs depend on the current state and the inputs, and a Moore state machine, where outputs depend only on the current state. Below are two diagrams representing Mealy and Moore state machines respectively.


![[Pasted image 20250614161458.png]]

![[Pasted image 20250614161511.png]]

In digital system design, finite state machines help visualize how your logic interacts to produce an output. It's very useful to start by creating a state diagram to visualize how your system moves from state to state before trying to draw gates/flip-flops or implementing your system with an HDL like SystemVerilog.

A great example of finite state machines can be found in sequence detectors. 
