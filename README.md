# 8-bit-Psuedorandom-Number-Generator
Design and implement  an  8-bit  pseudo  random  number generator on the Basys 3 board using Vivado. 

  A Linear Feedback Shift Register (LFSR) is a shift register with two or more of the flip-flop outputs XORed together and fed back to the input of the shift register. The inputs to the XOR gate are referred to as taps. For an n-bit shift register there are 2n-1 possible binary patterns which can be output. The value of all 0s is omitted as it will always repeat itself. Depending on the choice of taps there may be multiple  sequences  with  varying  lengths.  For  some  set  of  taps  we  will  generate  maximal  length sequence of all 2n-1 possible patterns.
  This arrangement is also called a pseudo-random number generator since the shift register outputs will appear  to  be  a  sequence  of  binary  random  numbers. The  set  of  taps  which  generates  the  maximal sequence for shift registers of n= 4 to 32 bits can be found in Roth et al (2016).
For this lab we will construct an 8-bit linear feedback shift register. The blockdiagramofthis LFSRis shownin the figure below.

![image](https://user-images.githubusercontent.com/88007099/127233295-4510310e-0a50-404a-9c30-ee891597b187.png)

  TheBasys 3board has a100MHz connected to pin W5 of the Artix-7 FPGA.However,this frequency is far too fast for us to see the pseudo-random sequence output from the shift register,so we use a clock divider to reduce the frequency to about 1 Hz.Thus,the counter will count once per second.
  To implement the 8-bit LFSR  we  will  use  three modules.The first module is the clock divider,the second block is an 8-bit LFSR that models the shift register with XOR feedback, and the third block is a top-level module that instantiates and interconnects the clock divider and the LFSR. This top level block can be synthesized and downloaded into the FPGA. A constraints file will connect the outputs to 8 leds and the reset to a push button.With this initial arrangement you will be able to see the 8-leds display a new, seemingly random, 8-bit value appear every second.
