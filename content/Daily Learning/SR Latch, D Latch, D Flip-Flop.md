Today I reinforced what I already knew about logic gates and timing circuits by learning about basic latches and the D flip-flop. 

### SR Latch
The SR latch comprises of two NOR gates with one gate's output connected to the other gates input. The remaining inputs are then connected to what is called the "set" and "reset" switches of the latch (hence the name SR).  The set switch turns the output high, and the reset switch turns the output low. However, the main defining feature of the SR latch is that once set or reset, continuing to press set or reset will not alter the state of the output. 
![[Pasted image 20250521150603.png]]
The SR latch, based on the way it is set up, also contains an invalid condition, which is when both set and reset are logic high at the same time. 

### D Latch with Enable
The D latch with enable comprises of a circuit similar to the SR latch, except with two changes. First, the "enable" switch makes an appearance, which is tied to one input of two different AND gates. The outputs of these AND gates feed into the NOR inputs that the old set and reset switches used to occupy. On the other inputs of the AND gates is the D switch, which replaces the set and reset switches. The output of this switch feeds into the two AND gates with a NOT gate on one input to simulate the old set and reset switches with a singular switch.
![[Pasted image 20250521151419.png]]
When enable is low, switching the D switch on and off does not affect the output at all. However, when enable is high, toggling the D switch acts just as the set and reset pins would on an SR latch. From what I've learned, the enable is a fundamental idea in digital electronics. The enable can be tied to a clock signal, and be switched on and off periodically. 

### D Flip-Flop
The D flip-flop takes the fundamental idea of a D latch with enable and combines it with a clock. Essentially, the output "Q" will change its output based on the state of the input "D", but will only do so at the rising edge of the clock, or when the clock switches from 0 to 1. This means that the flip-flop doesn't care what the state of D is at any time during the clock cycle, except for the instantaneous moment where the clock signal switches on. At that instant, the output Q will reflect the state of the input D and update. This allows for the D flip-flop to be one of the most instrumental digital memory component in digital design.

![[Pasted image 20250521152420.png]]