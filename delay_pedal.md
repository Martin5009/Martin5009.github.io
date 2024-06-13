---
layout: page
title: Digital Delay Pedal
permalink: /delay_pedal/
---

# Summary
  This ongoing project is my first practical venture (albeit a relatively safe one) into the field of digital signal processing. The goal is to design, build, and test a digital delay pedal with adjustable feedback and mix. I intend to use my ICE40UP5K FPGA from the arcade cabinet project as the digital audio processor, and separate ADC/DAC ICs to convert the audio signal to and from digital. Figure 1 shows a system-level block diagram of the planned design, where Km and Kf are the mix and feedback gains. Currently I have designed the digital delay unit at the register transfer level and verified its functionality using ModelSim. The next steps are to verify functionality in hardware, then start on the analog signal processing circuitry.

# Problem Statement
  Building the delay pedal involves designing and integrating multiple sub-systems, including any analog signal conditioning circuitry at the audio input and output, the ADC and DAC, and the digital delay unit itself. Figure 1 shows how I plan to connect these subsystems. I predict the brunt of the design work to be in the digital delay unit, as I must not only implement the digital delay, but also interface the delay unit with the 12-bit ADC and DAC ICs, both of which use SPI to send/receive digital audio data. I must continually reference the ADC and DAC datasheets to ensure that my delay unit complies with the manufacturer's timing specifications. The next challenge is to condition the analog signal at the audio input and output. I am designing this pedal to be used with an electric guitar, and I expect a guitar to produce a signal containing negative and positive voltages. As of now, I have no way to produce a negative voltage rail, so I will need to use a virtual ground as a midpoint reference. Using a virtual ground in this way will also require me to bias and amplify the audio signal such that it is centered about this midpoint reference.

<div style="text-align: left">
  <img src="../assets/delay_pedal_block_diagram.png" alt="logo1" width="900" />
</div>

Fig 1. System-level block diagram for an FPGA-based digital delay pedal.

# Digital Delay Unit
<div style="text-align: left">
  <img src="../assets/digital_delay_unit.png" alt="logo1" width="900" />
</div>

Fig 2. Block diagram of the digital delay unit at the register transfer level

<div style="text-align: left">
  <img src="../assets/digital_delay_unit_fsm.png" alt="logo1" width="900" />
</div>

Fig 3. Finite state machine showing the high-level behavior of the digital delay unit.


