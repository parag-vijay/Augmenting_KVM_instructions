# Augmenting_KVM_instructions

The aim is to augment KVM to allow previously unused opcodes/instruction byte sequences to be
used as new instructions, as outlined below.

All instructions in the x86 ISA are represented by sequences of bytes in memory. These sequences are
called opcodes and vary in length between 1 and 15 bytes. Not all sequences of bytes are meaningful – any
byte sequence that does not map to a valid instruction generates an #UD (Undefined Instruction) exception.
If these undefined instructions are executed in usermode, the guest OS kernel will typically trap theexception and kill the offending process with SIGILL (Illegal Instruction). If these undefined instructions
are executed in the kernel, the kernel may panic or crash (depending on the guest OS).
