
Resources: 
- https://florian.github.io//xor-trick/
- https://leetcode.com/discuss/study-guide/2960396/Bit-Manipulation-Guide-and-Tricks
- https://leetcode.com/discuss/interview-question/3695233/all-types-of-patterns-for-bits-manipulations-and-how-to-use-it

There are 6 types of bitwise operators:

- and (&)
    - Here each bit is multiplied
    - 1 * 1 = 1
    - 1 * 0 = 0
    - 0 * 0 = 0
    - 0 * 1 = 0
    - example: 1001 & 1100 = 1000
- or (|)
    - Each bit is added with other
    - 1 + 1 = 1
    - 1 + 0 = 1
    - 0 + 1 = 1
    - 0 + 0 = 0
    - example: 1001 | 1100 = 1101
- xor (^)
    - If same then 0, if different then 1
    - 1 ^ 0 = 1
    - 1 ^ 1 = 0
    - 0 ^ 0 = 0
    - 0 ^ 1 = 1
    - example: 1001 ^ 1100 = 0101
- complement (~)
    - Inverts all bits of binary representation
    - example : 0101 = 1010
- left shift (<<)
    - Shifts the value to the left in binary representation
    - example: 0011 << 1 = 0110
    - here the represenation is shifted towards left by 1
- right shift (>>)
    - Shifts the value to the right in binary representation
    - example: 1100 >> 1 = 0110
    - here the represenation is shifted towards right by 1

_Complement is probably the most least used bitwise operator._

---

_Important note - To just clear the confusion I m using end and start like this - forEx(0001) 1 is at the end and 0 is at the start._

- In binary form of any number every
    
    - even number ends with `0`
    - odd number ends with `1`
    - power of 2 has only `1` bit. For ex - `16 = 10000`
- Divide by 2 operation is similar to right shift by 1.
    
    - (`14 / 2 = 7` is same as `14(1110) >> 1` = `0111`. Here `0111` == `7`)
- Power Operation
    
    - Power of 2 `(1 << x)`
- Xor Operation
    
    - a ^ b = c, c ^ a = b, c ^ b = a
