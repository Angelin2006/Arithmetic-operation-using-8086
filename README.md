# Arithmetic-operation-using-8086
# 8086 Assembly Language Programs for Arithmetic Operations

## AIM

To write and execute Assembly Language Programs to perform arithmetic operations for the 8086 microprocessor.

---

## APPARATUS REQUIRED

* Personal Computer with MASM Software

---

## 1. ADDITION

#### Algorithm

1. Initialize memory location in HL register.
2. Store 1st data.
3. Increment HL to enter 2nd data.
4. Move 2nd number to accumulator.
5. Decrement HL.
6. Add value in memory with accumulator.
7. Store result.
8. Stop.


## FLOW CHART
<img width="707" height="1024" alt="image" src="https://github.com/user-attachments/assets/b5a7062d-e294-47cd-9683-a40de25e82de" />


#### Program

```asm
CODE SEGMENT
ASSUME CS:CODE, DS:CODE

ORG 1000H

START:
    MOV AX, CODE
    MOV DS, AX

    MOV SI,2000H
    MOV DX,0000H

    MOV AX,[SI]
    MOV BX,[SI+02H]

    ADD AX,BX

    MOV [SI+04H],AX
    MOV [SI+06H],DX

    MOV AH,4CH
    INT 21H

CODE ENDS
END START


```

#### Output Table

| MEMORY LOCATION (INPUT) | MEMORY LOCATION (OUTPUT) |
| ----------------------- | ------------------------ |
|      2000:08            |        2004:06           |
| ----------------------- | ------------------------ |
|      2001:00            |        2005:00           |
| ----------------------- | ------------------------ |
|      2002:04            |        2006:00           |
| ----------------------- | ------------------------ |
|      2003:00            |        2007:00           |
| ----------------------- | ------------------------ |

#### Manual Calculations

<img width="810" height="421" alt="Screenshot 2026-02-12 113251" src="https://github.com/user-attachments/assets/cf56d7da-00e1-4381-b9ab-aa64ff149c33" />


---

## OUTPUT IMAGE FROM MASM SOFTWARE

<img width="630" height="431" alt="Screenshot 2026-01-30 110848" src="https://github.com/user-attachments/assets/3bbb5c8d-a923-4ca2-85ee-af2045ef4dd1" />

## 2. SUBTRACTION

#### Algorithm

1. Initialize memory and store 1st data.
2. Increment to get 2nd data.
3. Move 2nd data to accumulator.
4. Subtract memory content.
5. Store result.

## FLOWCHART

<img width="578" height="797" alt="image" src="https://github.com/user-attachments/assets/564c3c7a-33ce-4a1c-8920-beb5c24b9b47" />


#### Program

```asm

    CODE SEGMENT
    ASSUME CS:CODE, DS:CODE

    ORG 1000H

    START:
    MOV AX, CODE
    MOV DS, AX

    MOV SI,2000H
    MOV DX,0000H

    MOV AX,[SI]
    MOV BX,[SI+02H]

    SUB AX,BX

    MOV [SI+04H],AX
    MOV [SI+06H],DX

    MOV AH,4CH
    INT 21H

    CODE ENDS
    END START

```

#### Output Table

| MEMORY LOCATION (INPUT) | MEMORY LOCATION (OUTPUT) |
| ----------------------- | ------------------------ |
|      2000:08            |        2004:04           |
| ----------------------- | ------------------------ |
|      2001:00            |        2005:00           |
| ----------------------- | ------------------------ |
|      2002:04            |        2006:00           |
| ----------------------- | ------------------------ |
|      2003:00            |        2007:00           |
| ----------------------- | ------------------------ |

#### Manual Calculations

(Add your calculation here)

<img width="1280" height="985" alt="image" src="https://github.com/user-attachments/assets/60192119-c88f-4d29-920a-a1b679512d19" />


## OUTPUT SCREEN FROM MASM SOFTWARE

<img width="630" height="421" alt="Screenshot 2026-01-23 104654" src="https://github.com/user-attachments/assets/7ef200fe-4aa0-448b-91e8-a6f3c10d5e4c" />

## 3. MULTIPLICATION

#### Algorithm

1. Initialize memory and store operands.
2. Move operands to registers.
3. Multiply.
4. Store result.

##FLOWCHART

<img width="569" height="906" alt="image" src="https://github.com/user-attachments/assets/88be88ff-2896-4a88-b73d-84ccffd2fcf9" />



#### Program

```asm
CODE SEGMENT
ASSUME CS:CODE, DS:CODE

ORG 1000H

START:
    MOV AX, CODE
    MOV DS, AX

    MOV SI,2000H
    MOV DX,0000H

    MOV AX,[SI]
    MOV BX,[SI+02H]

    MUL BX

    MOV [SI+04H],AX
    MOV [SI+06H],DX

    MOV AH,4CH
    INT 21H

CODE ENDS
END START


```

#### Output Table

| MEMORY LOCATION (INPUT) | MEMORY LOCATION (OUTPUT) |
| ----------------------- | ------------------------ |
|      2000:0A            |        2004:14           |
| ----------------------- | ------------------------ |
|      2001:00            |        2005:00           |
| ----------------------- | ------------------------ |
|      2002:05            |        2006:00           |
| ----------------------- | ------------------------ |
|      2003:00            |        2007:00           |
| ----------------------- | ------------------------ |

#### Manual Calculations

<img width="1280" height="1082" alt="image" src="https://github.com/user-attachments/assets/64c50523-45d9-4445-8abd-dee07b2f3f31" />


## OUTPUT SCREEN FROM MASM SOFTWARE

<img width="654" height="418" alt="Screenshot 2026-01-30 112451" src="https://github.com/user-attachments/assets/13df456f-ae6a-46be-85c2-1c0ec90e9546" />

## 4. DIVISION

#### Algorithm

1. Load memory location of operands.
2. Perform division.
3. Store result.

   ## FLOWCHART
<img width="1065" height="802" alt="image" src="https://github.com/user-attachments/assets/25b4a483-0d42-494b-8639-1af3ea17191b" />


#### Program

```asm
CODE SEGMENT
ASSUME CS:CODE, DS:CODE

ORG 1000H

START:
    MOV AX, CODE
    MOV DS, AX

    MOV SI,2000H
    MOV DX,0000H        ; IMPORTANT: clear DX before DIV

    MOV AX,[SI]         ; Dividend (16-bit)
    MOV BX,[SI+02H]     ; Divisor (16-bit)

    DIV BX              ; DX:AX / BX
                        ; Quotient -> AX
                        ; Remainder -> DX

    MOV [SI+04H],AX     ; Store quotient
    MOV [SI+06H],DX     ; Store remainder

    INT 3               ; <-- stop here for DEBUG

CODE ENDS
END START

```

#### Output Table

| MEMORY LOCATION (INPUT) | MEMORY LOCATION (OUTPUT) |
| ----------------------- | ------------------------ |
|      2000:0A            |        2004:02           |
| ----------------------- | ------------------------ |
|      2001:00            |        2005:00           |
| ----------------------- | ------------------------ |
|      2002:05            |        2006:00           |
| ----------------------- | ------------------------ |
|      2003:00            |        2007:00           |
| ----------------------- | ------------------------ |

#### Manual Calculations

<img width="1280" height="381" alt="image" src="https://github.com/user-attachments/assets/946ee29d-8ef6-4d91-ae5e-5661cc239861" />

---
## OUTPUT FROM MASM SOFTWARE

<img width="610" height="411" alt="Screenshot 2026-01-30 113045" src="https://github.com/user-attachments/assets/e4c41987-0c6f-4407-bb6c-23af2a43d7b3" />

## RESULT

Thus, the Assembly Language Programs for 8086 to perform arithmetic operations (Addition, Subtraction, Multiplication, and Division) using both direct and indirect methods were successfully written and executed using MASM.
