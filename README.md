# DAC
 INTERFACING DAC WITH 8086 KIT AND GENERATING SAWTOOTH AND SQUARE WAVEFORMS

## AIM
To write an assembly language program in 8086 to generate Sawtooth and Square waveforms using DAC.

---

## APPARATUS REQUIRED

| S. No | Item              | Specification   | Quantity |
|-------|------------------|-----------------|----------|
| 1     | Microprocessor kit | 8086            | 1        |
| 2     | Power Supply      | +5 V DC, +12 V DC | 1      |
| 3     | DAC Interface board | -              | 1        |

---

## ALGORITHM
## Algorithm – Sawtooth Waveform

1. Start.
2. Initialize the 8255 PPI with Port A as output.
3. Load `00H` into register `AL`.
4. Send the contents of `AL` to the DAC through Port A.
5. Increment the contents of `AL`.
6. Repeat steps 4 and 5 until `AL` reaches `FFH`.
7. Reset `AL` to `00H`.
8. Repeat the process continuously to generate the sawtooth waveform.
9. Stop.

## Algorithm – Square Waveform

1. Start.
2. Initialize the 8255 PPI with Port A as output.
3. Load `00H` into register `AL`.
4. Send `00H` to the DAC through Port A.
5. Introduce a delay.
6. Load `FFH` into register `AL`.
7. Send `FFH` to the DAC through Port A.
8. Introduce a delay.
9. Repeat steps 3 to 8 continuously to generate the square waveform.
10. Stop.
### Measurement of Analog Voltage
1. Send the digital value to DAC.  
2. Read the corresponding analog value at its output.  

### Waveform Generation

#### Square Waveform
1. Send low value (00) to the DAC.  
2. Introduce suitable delay.  
3. Send high value to DAC.  
4. Introduce delay.  
5. Repeat the above procedure.  

#### Sawtooth Waveform
1. Load low value (00) to accumulator.  
2. Send this value to DAC.  
3. Increment the accumulator.  
4. Repeat step (ii) and (iii) until accumulator value reaches FF.  
5. Repeat the above procedure from step 1.  

---

## PROGRAMS
```
ORG 1000H

START:  MOV AL,00H
        OUT 0C8H,AL
        CALL DELAY

        MOV AL,0FFH
        OUT 0C8H,AL
        CALL DELAY

        JMP START

DELAY: MOV CX,0505H
L1:    DEC CX
       JNZ L1
       RET

END
```

# 8086 Assembly Programs – DAC Interfacing
 

## Program: Square Wave

| Memory Location | Program     | Comments                          |
|-----------------|-------------|-----------------------------------|
| 1000            | MOV AL,00H  | Load 00H in Accumulator           |
| 1003            |  OUT 0C8H,AL | Send through output port         |
| 1005            |  CALL DELAY(1100)  | CALL PROGRAM TO 1100      |
| 1008            |  MOV AL,0FFH |   Load 00H in Accumulator       |
| 100A            |   OUT 0C8H,AL|  Send through output port       |
| 100D            |  CALL DELAY(1100) | CALL PROGRAM TO 1100       |


| Memory Location | Program     | Comments                          |
|-----------------|-------------|-----------------------------------|
| 1100            | MOV CX,0505  | Load 0505H in Accumulator           |
| 1103            |  DEC CX | Decrement CX        |
| 1105           |  JNZ 1104  | RPEAT UNTILL ZERO      |
| 1108            |   RET |   RETURN TO MAIN PROGRAM      |


# Program: Sawtooth wave
ORG 1000H

START: MOV AL,00H

LOOP1: OUT 0C8H,AL
       INC AL
       JNC LOOP1
       JMP START

END

## Assembly Program

| Memory Location | Program Instruction   | Comments                        |
|-----------------|-----------------------|---------------------------------|
| `1000`          | `START: MOV AL,00H`  | Load `00H` in accumulator       |
| `1003`          | `LOOP : OUT 0C8H,AL` | Send through output port        |
| `1005`          | `INC AL`             | Increment contents of accumulator |
| `1007`          | `JNC LOOP`           | Jump if no carry (continue loop) |
| `1009`          | `JMP START`          | Go to starting location         |

---

## Tabulation

| Waveform  | Amplitude | Time period | 
|-----------|-----------|-------------|
| Sawtooth  |           |             | 
| Square    |           |             |
---

## Model Graph


<img width="1523" height="860" alt="image" src="https://github.com/user-attachments/assets/28fa41ff-8dc2-46ad-9d6d-df99bd2468f2" />




## OUTPUT IMAGE OF DAC(SAWTOOTH WAVE FROM DSO AND SQUARE WAVE FROM DSO)

**Voltage
  5V  ┌──────┐      ┌──────┐      ┌──────┐
      │      │      │      │      │      │
  0V  └──────┴──────┘      └──────┴──────┘
          Time →**
Voltage
  5V       /|       /|       /|
          / |      / |      / |
         /  |     /  |     /  |
  0V  ──/   └────/   └────/   └──
          Time →


## Result

Thus, the **DAC was interfaced with 8086** and different **waveforms** were successfully generated.




