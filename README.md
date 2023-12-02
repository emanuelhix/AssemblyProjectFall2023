## Assembly Project CS3203 Fall 2023 ##

# Instruction Set #

 Assembly Language for CS 317

 There are three groups of instructions:
	Memory Reference Instructions
	Non memory Reference Instructions
	Pseudo Instructions (i.e., Assembler directive instructions)

 Memory Reference Instructions (MRI)


 Direct Addressing:	opcode operand	e.g., ADD num
	Memory word at location 'num' is added to accumulator AC. I.e., AC = AC + M[num];
	Here, effective address of the operand is 'num'

 Indirect Addressing: opcode operand I	e.g., ADD num I
	Memory word of memory word at location 'num' is added to AC. I.e., AC = AC + M[M[num]]
	Here, effective address of the operand is M[num].


 MRI Instructions: (In the following, 'eee' denotes effective address.)

 AND xxx		AND xxx I
 Logical AND of effective memory word to AC.
 I.e., AC = AC and M[eee];

 ADD xxx		ADD xxx I
 Add effective memory word to AC.
 I.e., AC = AC + M[eee];

 LDA xxx		LDA xxx I
 Load effective memory word to AC.
 I.e., AC = M[eee];

 STA xxx		STA xxx I
 Store content of AC to effective memory word.
 I.e., M[eee] = AC;

 BUN xxx		BUN xxx I
 Branch, unconditionally, to effective address.
 I.e., PC = eee;

 BSA xxx		BSA xxx I
 Address of next instruction (i.e., PC) is stored in effective memory word.
 Then, execute the instruction following the effective address.
 I.e., M[eee] = PC; PC = eee + 1;
 Note:	BSA is useful to save the return address and to branch to a procedure.

 ISZ xxx		ISZ xxx I
 Increment memory word. If incremented value is 0, increment PC (i.e., skip next instr).
 I.e., M[eee] = M[eee] + 1; if (M[eee] == 0) PC = PC + 1;
 Note:	ISZ is used to count iterative loops.


 Non Memory Reference Instructions
 These instructions do not have the operand part or the addressing mode.

 CLA	Clear AC

 CLE	Clear E, the extended bit of AC

 CMA	Complement AC

 CME	Complement E

 CIR	Circular shift to the Right on AC and E

 CIL	Circular shift to the Left on AC and E

 INC	Increment AC

 SPA	Skip next instruction, if AC is Positive, i.e., if (AC > 0) PC = PC + 1;

 SNA	Skip next instruction, if AC is Negative, i.e., if (AC < 0) PC = PC + 1;

 SZA	Skip next instruction, if AC is Zero, i.e., if (AC == 0) PC = PC + 1;
	(Note: SPA, SNA, and SZA are used in conditional branching.)

 SZE	Skip next instruction, if E is Zero, i.e., if (E == 0) PC = PC + 1;

 HLT	Halt the execution

 INP	Input a character from INPR to low-order bits of AC

 OUT	Output a character from low-order bits of AC to OUTR

 SKI	Skip on Input flag (It is not used in this assembler.)

 SKO	Skip on Output flag (It is not used in this assembler.)

 ION	Interrupt On (It is not used in this assembler.)

 IOF	Interrupt Off (It is not used in this assembler.)


 Pseudo Instructions

 ORG hhh		Instruction listed in the following line wll be placed at address 'hhh' (Hex)

 DEC n	Decimal number 'n' will be placed in the memory word

 HEX n	Hexadecimal number 'n' will be placed in the memory word

 END	Denotes the end of assembly language source program

 (Refer to Sections 5.3, 5.5, 5.6, 5.7, 6.3 of Computer System Architecture (3e)
  by M. Morris Mano, for details.)

