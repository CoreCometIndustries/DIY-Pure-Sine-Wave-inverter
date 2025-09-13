# DIY-Pure-Sine-Wave-inverter
Designed by: Core Comet Industries Pvt. Ltd.
Platform: Arduino UNO / ATmega328P
PWM Frequency: ~17.7kHz (ICR1 = 900)
Output: Pure sine wave (via 180-step lookup table)
Features: Feedback-based voltage regulation, low battery cutoff, short-circuit protection, and manual ON/OFF control.

📁 Project Overview
This project implements a pure sine wave inverter using an Arduino-compatible microcontroller. The waveform is generated using a 180-step sine lookup table with Phase Correct PWM using Timer1. Feedback control is implemented to regulate voltage and protect against unsafe conditions.

⚙️ Features
✅ Pure sine wave output (via PWM lookup table)
⚙️ Dynamic feedback control to stabilize output voltage
🔋 Low battery protection
⚠️ Short-circuit detection
🔘 Push-button controlled ON/OFF switching
🚨 Auto shutdown with LED blinking alert
🔄 Restart system on button press

🧠 How It Works
PWM Generation: Timer1 in Phase Correct mode drives two output pins alternately (OCR1A, OCR1B) to produce a full sine wave using sinPWM[] table.
Feedback Control: The voltage is read from analog pin A1. Based on the feedback, a gain factor h is adjusted dynamically to maintain output voltage stability.

Protections:
Low Battery: If analog reading from A0 (battery) drops below 575, inverter shuts down.
Short Circuit: If feedback voltage is low and output gain h is maxed out (> 0.99), the system assumes short and shuts down.

Button Controls:
Start: Press button connected to digital pin 12 to start the inverter.
Stop: Press the button again to stop the inverter or reset after protection.




🧪 Tested With
Arduino UNO R3
IR2110 MOSFET Driver
12V Lead Acid Battery
Oscilloscope for waveform analysis

🛡️ Protections & Safety
Condition	Action
Battery < 575 (ADC)	Auto shutdown, LED blink
Feedback voltage < 100 + h>0.99	Assumes short, auto shutdown
Button Press	Manual ON/OFF or restart

🔄 Example Serial Output
Button press
Inverter running...
Low battery detected!
Short circuit condition!

🧾 How to Use
Upload the code to Arduino UNO.
Connect output stage (MOSFETs, transformer, etc.).
Connect feedback and battery sense lines to A1 and A0.
Press button to start the inverter.
Observe waveform on output using oscilloscope.
Press button again to shut down.

🏢 About
Core Comet Industries Pvt. Ltd.
Innovating at the intersection of AI, Electronics, and Space-tech.
This inverter project is part of our mission to build smart energy systems for the future.
