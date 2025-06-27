


1. **What is the structure of program memory stack?**

**Text Segment**
stores the code to be executed

**Data Segment**
stores static/global variables initialized by programmer 

**BSS segment**
Stores uninitialized static/global variables

**Heap**
space for dynamic memory allocation

**Stack**
used for storing the good old local variables defined inside functions / data for function calls like return addresses, arguments ect.




	1. What is the structure of the stack itself?
	
**The stack itself**
High memory address -----------------> low memory address

Parameters/Passed Arguments -> EIP/Return address -> EBP/Stack Pointer -> Local Variables -> Free memory


		


3. **What are the roles of EIP and EBP registers?**

**EIP** = Return Address - register holds the address of the memory location to return to once the current function has finished

EBP = Stack Pointer -  reference point for the rest of the stack


- they are 32 bit system registers, known as RIP and RBP in 64-bit systems
- each are 4-bytes long and store addresses in either little or big endian ways


4. **What's the difference between Big endian vs Little endian, and can you identify them visually, quickly?**

so if there's a hex value 0x012160c1

**The big endian (normal reading):**

\x01\x21\x60\xc1

**The little endian (Arabian reading):**

\xc1\x60\x21\x01



5. **What is the stack layout for a function call?**

![[Pasted image 20250512171145.png]]


6. **What is Vulnerable program analysis?**





7. **What are the consequences of buffer overflow?**

	**Overwriting return address with a different address can point to**

		- invalid instruction
		- Non-existing address
		- Access violation
		- Attacker's code --> malicious code to gain access


8. **How is buffer overflow achieved?**


the AAAAAAAAAAA stuff overwrites/eats into the EBP/Return address and EIP/Stack pointers, causing the program to crash when the function ends. 

the AAA... eats into the memory for EBP/EIP, going further up into buffer territory/outside of usual stack territory/higher up in the memories address. remember stack grows down and heap grows up


9. **What are some countermeasures to buffer overflow?**


**Developer approaches**
use safer functions: strncpy_s()

**OS approaches**
ASLR (address space layout randomization)
To randomize the start location of the stack that is every time the code is
loaded in the memory, the stack address changes.

**Compiler approaches**
stack guard

**Hardware approaches**
non-executable stack