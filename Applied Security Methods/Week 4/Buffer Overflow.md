**[Week 4 Slides](https://modules.lancaster.ac.uk/pluginfile.php/3929559/course/section/462271/4%20Code%20Execution.pdf)**
### Program memory stack
![[Pasted image 20250206115820.png]]

- text segment: stores the executable code of the program. This block of memory is usually read-only.

- Data segment: stores static/global variables that are initialized by the programmer

- BSS segment: stores uninitialized static/global variables

- Heap: the heap is used to provide space for dynamic memory allocation

- Stack: used for storing local variables defined inside functions, as well as storing data related to function calls, such as return address, arguments ... 

#### Stack (simplified)

![[Pasted image 20250206120247.png]]




##### EIP and EBP CPU registers

EIP - register that holds the address of the memory location to return to once the current function has finished

EBP - a register that is essentially used as a reference point for the rest of the stack

EIP and EBP are 32-bit system registers, they are known as RIP and RBP in 64-bit systems

EIP and EBP are 4 bytes each, storing addresses that look like 0x666574c9

big endian: \x66\x65\x74\x9

little endian: \xc9\x74\x65\x66


##### Order of function arguments in the stack

foo(a,b)
int x,y
x =a+b
y=a-b
![[Pasted image 20250206121350.png]]


**The local variables and function**
**arguments are stored in the stack with**
**reference to ebp. The argument ‘b’ is**
**stored at a higher address and hence is**
**pushed into the stack before. The**
**function arguments are pushed into the**
**stack in reverse order**

###### Function call stack

![[Pasted image 20250206121530.png]]


![[Pasted image 20250206121628.png]]




### Vulnerable Program

//

#### Consequences of Buffer Overflow

overwriting return address with a different address can point to :

- invalid instruction
- non-existing address
- access violation
- attacker's code --> Malicious code to gain access


#### How to run malicious code
//


### Countermeasures

Dev approaches:
- use of safer functions like strncpy_s(), strcat_s()
- safer dynamic link libraries that check the length of the data before copying
OS approaches:
- ASLR
compiler approaches:
- Stack-Guard
Hardware approaches
- non-executable stack


#### Principle of ASLR

- to randomize the start location of the stack that is every time the code is located in memory, the stack address changes
- Difficult to guess the stack address in the memory
- Difficult to guess %ebp address and address of the malicious code


#### Stack guard
![[Pasted image 20250206123638.png]]


#### Non-executable stack


- NX bit, is a feature in CPU separates code from data which marks certain areas of the memory as non-excecutable
- this countermeasure can be defeated using a different technique called return-to-libc attack
- do a buffer overflow, such that the return address is a libc function such as system