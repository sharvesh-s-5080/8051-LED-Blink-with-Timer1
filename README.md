# 8051-LED-Blink-with-Timer1
8051 Assembly Program to Blink an LED Using Timer1 Mode1 with 250ms Delay
# Aim:
To write and simulate an Assembly Language Program using the 8051 microcontroller to blink an LED
connected to Port 0.5 with a 250 millisecond delay, using Timer1 in Mode1.
# Software required:
Keil μVision IDE
8051 Assembler (A51)
# Algorithm:
1.Configure Timer1 in Mode 1 (16-bit) using TMOD. 2.Load TH1 and TL1 with values for ~50 ms delay.
3.Repeat the timer delay 5 times to get ~250 ms. 4.Toggle the LED connected to P0.5. 5.Repeat the
process infinitely.
# Program:
```
ORG 0000H
START: 
CLR P0.5
MOV TMOD,#10H
AGAIN:
MOV R2,#05
DELAY_LOOP:
MOV TH1,#3CH
MOV TL1,#0B0H
CLR TF1
SETB TR1
WAIT:
JNB TF1, WAIT
CLR TR1
CLR TF1
DJNZ R2, DELAY_LOOP
CPL P0.5
SJMP AGAIN
END
```
# Output image from keil software:

<img width="400" height="400" alt="Screenshot 2025-10-24 194136" src="https://github.com/user-attachments/assets/9f7b71c1-6323-4539-8268-4abf1d78b846" />

# Manual calulations:
Clock freq = 11.0592 MHz → 1 machine cycle ≈ 1.085 μs =50000 × 1.085 μs ≈ 54.25 ms
Loop 5 times → 5 × 50 ms ≈ 250 ms

# Observation:
Successfully created a delay of 250 ms using Timer1 in Mode 1.
Used assembly code to toggle P0.5, simulating LED blinking.
Simulated in Keil using the Port 0 window (logic level view).
Can be extended to real hardware or simulated in Proteus for visual confirmation.

# Result:
Thus, the 8051 Assembly Language Program to blink an LED with a 250 ms delay using Timer1 in Mode1.







































