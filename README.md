# Booth's Algorithm Project
#### Author: Jonah Yates

### _Abstract_
Booths Algorithm is a multiplication algorithm designed by Andrew Donald Booth in the 1950s. The algorithm is a method for performing multiplication on two binary numbers within an arithmetic logic unit (ALU). Its relevance is primarily due to the performance advantages it provides compared to the traditional add-and-shift since instead of checking one bit of the multiplier each iteration, the algorithm checks two bits and then uses a coding scheme. This makes Booths faster than add and shift on average since fewer additions are performed on average. The instance where add and shift would be faster than Booth’s is when we are dealing with alternating 0s and 1s within the multiplier.
### Introduction & Motivation
In computer systems, the arithmetic logic unit is the component tasked with performing the arithmetic and logic operations in instructions. Since many instructions computers are tasked with performing is math or logic-based, it is important to minimize the time impact the ALU is having on code execution. This leads to the need to have quick algorithms that perform a minimal number of operations to compute the desired data output. In terms of multiplication, there are several algorithms that can be used: repeated addition, add and shift, and Booth’s algorithms just to name a few. For improving the speed of each algorithm, the designer implements shortcuts. Like the add-and-shift algorithm, Booth’s algorithm works with signed magnitude numbers and the number of iterations is due to the length of the register the numbers are stored in. However, what we will be exploring in this project is the additional shortcut Booth employs: the ability to skip a series of 0s or 1s each iteration. We are curious about how the input impacts the number of additions and subtractions performed.

### Code Explanation
In the project, Booth’s algorithm was implemented in C++. The project begins by declaring the empty vectors: _AC_, _q_multiplier_, and _multiplicand_. The user is then prompted for the multiplicand and multiplier. As we receive each number, _length_ is computed and stored, the number is verified to be >= 4 bits and <= 12 bits in length, contains only 0s or 1s and finally, the string is parsed, and each bit added to the corresponding integer vector. The Booth’s algorithm function is then called and passed _q_multiplier_, _multiplicand_. Within the algorithm function, we will first compute and store the 2s complement of _multiplicand_ since subtracting the multiplicand can instead be performed via adding the 2s complement. Furthermore, we will use the fact that Booth’s algorithm runs for _length_ iterations. From here, in each iteration, we will look at the last 2 bits of _AC_ _Q_ _q0_ and use the following coding scheme to decode the bits and execute the corresponding action.
- 00 – no action
- 01 – add multiplicand
- 10 – sub multiplicand (add 2s complement)
- 11 – no action 

Before the end of each iteration, an arithmetic shift right is also performed. This is also the reason why vectors were used; vectors allow indexing at certain positions and updating values, making shifting easy. Finally, once we exit the loop the result which is in _AC_ _Q_ is returned.

### View the report pdf to view the full report.
