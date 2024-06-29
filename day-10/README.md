# 100 Days Verification Challenge - Day 10

## 1. Types of Number Systems

There are four main types of number systems used in digital electronics and computing:

### 1. Decimal Number System
- Base: 10
- Digits: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
- Usage: It is the most commonly used number system in daily life.
- Representation: Each digit is a power of 10. For example, 345 can be represented as \(3 \times 10^2 + 4 \times 10^1 + 5 \times 10^0\).

### 2. Binary Number System
- Base: 2
- Digits: 0, 1
- Usage: Used in computers and digital systems.
- Representation: Each digit is a power of 2. For example, 1011 can be represented as \(1 \times 2^3 + 0 \times 2^2 + 1 \times 2^1 + 1 \times 2^0\).

### 3. Octal Number System
- Base: 8
- Digits: 0, 1, 2, 3, 4, 5, 6, 7
- Usage: Sometimes used in computing as a shorthand for binary.
- Representation: Each digit is a power of 8. For example, 157 can be represented as \(1 \times 8^2 + 5 \times 8^1 + 7 \times 8^0\).

### 4. Hexadecimal Number System
- Base: 16
- Digits: 0-9 and A-F (where A=10, B=11, C=12, D=13, E=14, F=15)
- Usage: Widely used in computing and digital electronics as a compact representation of binary.
- Representation: Each digit is a power of 16. For example, 1A3 can be represented as \(1 \times 16^2 + 10 \times 16^1 + 3 \times 16^0\).

## 2. Explanation of Codes

### i. BCD (Binary-Coded Decimal) Code
- Description: BCD code is a binary-encoded representation of integer values that uses a 4-bit nibble to represent each decimal digit.
- Example: The decimal number 59 is represented in BCD as 0101 1001.

### ii. Gray Code
- Description: Gray code, also known as reflected binary code, is a binary numeral system where two successive values differ in only one bit.
- Usage: Minimizes errors in digital communication and in the processing of analog signals.
- Example: The sequence for the first few decimal numbers in Gray code is 0 (000), 1 (001), 2 (011), 3 (010), etc.

## 3. Applications

### i. Weighted Code
- Description: Each digit in the code represents a specific weight.
- Applications: Used in digital systems and computer arithmetic.
- Example: BCD is a type of weighted code.

### ii. Non-weighted Code
- Description: The code does not follow a positional weight pattern.
- Applications: Used in error detection and correction.
- Example: Gray code is a type of non-weighted code.

### iii. Excess-3 Code
- Description: A binary-coded decimal code that is self-complementing and non-weighted. Each digit of a decimal number is represented by its corresponding 4-bit binary number plus 3.
- Applications: Used in some old digital systems and calculators for simplifying the design of arithmetic circuits.

### iv. BCD Code
- Applications: Used in digital clocks, calculators, and other digital systems where numerical data is displayed.

### v. Gray Code
- Applications: Used in analog to digital converters (ADCs), digital to analog converters (DACs), error correction in digital communication, and rotary encoders.

### vi. ASCII Code
- Description: American Standard Code for Information Interchange.
- Applications: Used in computers and digital devices to represent text and control characters.

### vii. Octal Number System
- Applications: Used in computer systems, specifically in the early days of computing, as a shorthand for representing binary numbers.

### viii. Hexadecimal Number System
- Applications: Used in programming, computing, and digital electronics for a compact representation of binary data.

## 4. Disadvantage of an 8-4-2-1 Code
- Description: 8-4-2-1 code, also known as BCD, is inefficient in terms of storage as it uses more bits than necessary to represent numbers.
- Disadvantage: It requires 4 bits to represent each decimal digit, which is less efficient compared to binary representation.

## 5. Different Ways to Represent a Negative Number

### 1. Sign-Magnitude Representation
- The most significant bit (MSB) indicates the sign (0 for positive, 1 for negative), and the remaining bits represent the magnitude.

### 2. One's Complement
- Inverts all the bits of the binary representation of the number to get the negative counterpart.

### 3. Two's Complement
- Inverts all the bits and adds one to the least significant bit (LSB). This method is widely used in computer systems.

### 4. Excess-N Notation
- Uses a fixed number (bias) added to the actual value to represent numbers. For example, Excess-128 for 8-bit numbers.

### 5. Signed Digit Representation
- Uses digits to represent numbers along with a sign digit.
