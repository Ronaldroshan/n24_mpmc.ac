
# 1 ms DELAY USING TIMER 0 IN MODE 1

## AIM
To generate a 1 ms delay using Timer 0 in Mode 1 (16-bit timer mode) in assembly language program in 8051.

---
## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision software

---
## Algorithm
1. Set the TMOD register to 01H to configure Timer 0 in Mode 1 (16-bit mode).
2. Calculate the 16-bit reload value for a 1 ms delay and load the high byte into TH0 and the low byte into TL0.
3. Set the TR0 bit to start Timer 0.
4. Continuously check the Timer 0 overflow flag (TF0). Wait until the flag is set, indicating that 1 ms has passed.
5. Once the overflow occurs, clear the TF0 flag to reset the timer for the next cycle.
6. Reload the TH0 and TL0 registers with the same 16-bit reload value to ensure the timer continues running.
7. If you want continuous delay, repeat steps 4 to 6. If done, clear the TR0 bit to stop the timer.


---
## PROGRAM

```
ORG 0000H           
START:  
MOV TMOD, #01H  
MOV TH0, #0xFC 
MOV TL0, #0x18 
SETB TR0       
DELAY_LOOP:
JNB TF0, DELAY_LOOP 
CLR TF0     
MOV TH0, #0xFC  
MOV TL0, #0x18 
SJMP DELAY_LOOP 
END

```
---
## OUTPUT:
<img width="1086" height="498" alt="image" src="https://github.com/user-attachments/assets/72e28dd2-73b7-4be9-a55b-141f3fcc554c" />
---

## RESULT:
Thus, 1 ms delay using Timer 0 in Mode 1 is generated successfully.
