# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.

## Apparatus Required:
 Laptop with internet connection

## Algorithm:

### For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
   
### Program:
```
LDA 4200H
MOV B,A
LDA 4201H
ADD B
STA 4300H
JC STORE_CARRY
HLT
STORE_CARRY:MVI A,01H
STA 4301H
HLT
```



### Output:
<img width="1796" height="832" alt="Screenshot 2025-08-28 100518" src="https://github.com/user-attachments/assets/b95fa545-067e-499a-9ed8-b8f4529e92fd" />


<img width="566" height="450" alt="Screenshot 2025-08-28 100546" src="https://github.com/user-attachments/assets/448c25e8-7149-490f-a562-63768e55e48d" />


### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.


### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
CMP C
JC SWAP
MOV B,A
MOV A,C
SWAP: SUB B
STA 4300H
HLT
```
### Output:
<img width="1833" height="648" alt="image" src="https://github.com/user-attachments/assets/2ef20289-52c2-45bc-81af-cef382cab787" />


<img width="466" height="467" alt="Screenshot 2025-08-28 101732" src="https://github.com/user-attachments/assets/b441ec53-2070-4467-a17a-bb3d817e61f7" />



### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
```
LDA 4200H
MOV C, A
LDA 4201H
MOV B,A
MVI A, 00H
LOOP: ADD C
DCR B
JNZ LOOP
STA 4300H
HLT
```



### Output:

<img width="1809" height="825" alt="Screenshot 2025-08-28 102604" src="https://github.com/user-attachments/assets/106865c4-7511-4b77-894d-bd3e1f80aaaa" />


<img width="530" height="508" alt="Screenshot 2025-08-28 102615" src="https://github.com/user-attachments/assets/58d6bc9f-a461-4b35-a627-6edc86075a99" />


### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.


### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B, A
MVI A, 00H
LOOP: MOV A,C
CMP B
JC END
SUB B
MOV C, A
INR D
JMP LOOP
END: MOV A, D
STA 4300H
MOV A, C
STA 4301H
HLT
```



### Output:

<img width="1804" height="865" alt="Screenshot 2025-08-28 103327" src="https://github.com/user-attachments/assets/5f5f7087-682f-4dd4-acf3-86961a59b974" />


<img width="547" height="500" alt="Screenshot 2025-08-28 103336" src="https://github.com/user-attachments/assets/9cd894a1-ec96-4eec-800c-ce338a2f2790" />



## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

