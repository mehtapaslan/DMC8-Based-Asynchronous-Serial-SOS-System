DMC8 Based Asynchronous Serial SOS System
Project Overview

This project implements an interrupt-driven SOS emergency signaling system developed using the DMC8 microprocessor and the DEEDS simulator. The system follows a hybrid architecture that combines polling for idle input detection and hardware timer interrupts for precise Morse code timing control.

The system consists of two independent processing units: a Sender Ship and a Rescue Station, which communicate through asynchronous serial communication.

Key Technical Concepts (Novelty)

Hybrid Architecture
Polling is used during idle operation to detect user input, while a timer-driven Interrupt Service Routine (ISR) located at address 0038h controls all time-critical SOS signaling.

Semantic Communication
Instead of transmitting raw timing pulses, the sender transmits ASCII characters ('S' – 53h, 'O' – 4Fh). This approach reduces communication overhead and improves modularity.

Decoupled Sender–Receiver Design
The receiver reconstructs the Morse code timing independently using its own hardware timer, ensuring robust operation under asynchronous conditions.

Finite State Machine (FSM)
A Finite State Machine with ten distinct states (0–9) is implemented to manage dots, dashes, and inter-symbol intervals.

Project Files

finalproject.pbs – Main DEEDS simulator circuit design
sender.mc8  – Source and machine code for the Sender Ship
receiver.mc8 – Source and machine code for the Rescue Station

How to Run the Project

Open the DEEDS Simulator.

Load the finalproject.pbs file.

Load sender.mc8 into the Sender Ship microprocessor.

Load receiver.mc8 into the Rescue Station microprocessor.

Start the simulation (Press F9).

Press the TEST button (Port IB) to verify local LED operation.

Press the SOS button (Port IA) to initiate SOS signaling.
