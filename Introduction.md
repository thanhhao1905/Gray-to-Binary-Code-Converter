
-----

# Gray to Binary Code Converter

## Introduction

This is a simple yet effective tool for converting **Gray code** to its equivalent **binary code**. 
Gray code, also known as reflected binary code (RBC), is a binary numeral system where two successive values differ in only one bit. 
This unique property makes Gray code incredibly useful in error prevention systems, position encoders, and other digital applications where multiple bit changes at once could lead to errors or ambiguities.

In contrast, standard binary code is the fundamental numbering system used in most computers and digital devices, where each bit represents a power of 2. Converting between these two code forms is essential in various circuit design and analysis scenarios.


## How It Works

The conversion process from Gray code to binary code is based on a straightforward rule:

1.  The **Most Significant Bit (MSB) of the binary code** is the same as the MSB of the Gray code.
2.  Each subsequent **binary bit** is calculated by performing an **XOR (exclusive OR)** operation between the previously calculated binary bit and the current Gray code bit.

Example: Converting Gray code `1101` to binary code:

  * **First Binary Bit (MSB):** `1` (same as the first Gray bit)
  * **Second Binary Bit:** `1` (previous binary bit) XOR `1` (current Gray bit) = `0`
  * **Third Binary Bit:** `0` (previous binary bit) XOR `0` (current Gray bit) = `0`
  * **Fourth Binary Bit:** `0` (previous binary bit) XOR `1` (current Gray bit) = `1`

Thus, Gray code `1101` corresponds to binary code `1001`.

-----
