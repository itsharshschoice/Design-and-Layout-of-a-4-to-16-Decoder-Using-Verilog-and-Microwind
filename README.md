
# **4-to-16 Decoder Layout in Microwind**

This repository contains the Verilog implementation, layout, and analysis of a 4-to-16 decoder using the Microwind tool. The project demonstrates the design, simulation, and optimization of a combinational digital circuit that decodes a 4-bit binary input into one of 16 unique output lines.

## **Introduction**

A 4-to-16 decoder is a combinational circuit that activates one of its 16 outputs based on the 4-bit binary input. It finds applications in memory address decoding, multiplexing, and data routing. This project showcases the design and implementation of such a decoder using Verilog and the Microwind layout tool.

## **Features**

- Implements a 4-to-16 decoder using Verilog.
- Generates CMOS layout using Microwind.
- Performs functional verification and performance analysis, including delay and propagation.

## **Design Overview**

### Logic Diagram
The 4-to-16 decoder circuit uses AND gates and inverters to implement its logic. Each output corresponds to a unique minterm of the 4-bit input.

![App Screenshot](https://github.com/itsharshschoice/Design-and-Layout-of-a-4-to-16-Decoder-Using-Verilog-and-Microwind/blob/main/Screenshots/Circuit.png?raw=true)

### Truth Table
The truth table maps each 4-bit input combination to one of the 16 outputs, ensuring only one output is active at any time.

![App Screenshot](https://github.com/itsharshschoice/Design-and-Layout-of-a-4-to-16-Decoder-Using-Verilog-and-Microwind/blob/main/Screenshots/Truth%20Table.png?raw=true)

### Verilog Code
The Verilog code is written in gate-level modeling and implements all necessary logic for the 4-to-16 decoder. Below is the module definition:

```verilog
module decoder_4_to_16 (
    input A3, A2, A1, A0,   // 4-bit input
    output D0, D1, D2, D3, D4, D5, D6, D7, D8, D9, D10, D11, D12, D13, D14, D15 // 16 outputs);

    wire nA3, nA2, nA1, nA0; // Not gates for each input
    // Inverting each input
    not (nA3, A3);
    not (nA2, A2);
    not (nA1, A1);
    not (nA0, A0);

    // AND gates for each output
    and (D0, nA3, nA2, nA1, nA0);  // 0000
    and (D1, nA3, nA2, nA1, A0);   // 0001
    and (D2, nA3, nA2, A1, nA0);   // 0010
    and (D3, nA3, nA2, A1, A0);    // 0011
    and (D4, nA3, A2, nA1, nA0);   // 0100
    and (D5, nA3, A2, nA1, A0);    // 0101
    and (D6, nA3, A2, A1, nA0);    // 0110
    and (D7, nA3, A2, A1, A0);     // 0111
    and (D8, A3, nA2, nA1, nA0);   // 1000
    and (D9, A3, nA2, nA1, A0);    // 1001
    and (D10, A3, nA2, A1, nA0);   // 1010
    and (D11, A3, nA2, A1, A0);    // 1011
    and (D12, A3, A2, nA1, nA0);   // 1100
    and (D13, A3, A2, nA1, A0);    // 1101
    and (D14, A3, A2, A1, nA0);    // 1110
    and (D15, A3, A2, A1, A0);     // 1111

endmodule

```

## **Implementation**

### RTL View
Generated using Quartus, showing the gate-level representation of the decoder.

![App Screenshot](https://github.com/itsharshschoice/Design-and-Layout-of-a-4-to-16-Decoder-Using-Verilog-and-Microwind/blob/main/Screenshots/RTL.png?raw=true)

### Transistor-Level Schematic (Microwind Layout)
Designed in DSCH03 for CMOS implementation, showcasing the transistor connections for each output.

![App Screenshot](https://github.com/itsharshschoice/Design-and-Layout-of-a-4-to-16-Decoder-Using-Verilog-and-Microwind/blob/main/Screenshots/Layout.png?raw=true)

## **Simulation and Results**

Below is the simulation of 4 to 16 decoder in Microwind

![App Screenshot](https://github.com/itsharshschoice/Design-and-Layout-of-a-4-to-16-Decoder-Using-Verilog-and-Microwind/blob/main/Screenshots/Simulation.png?raw=true)

Delay and Propagation Analysis

- Simulation results for each output line include:

    - Delay (Low-to-High): **Minimum: 27 ns, Maximum: 69 ns**
    - Delay (High-to-Low): **Minimum: 13 ns, Maximum: 76 ns**
    - Propagation Delay: **Average: 68 ns**

Voltages and Currents plot

![App Screenshot](https://github.com/itsharshschoice/Design-and-Layout-of-a-4-to-16-Decoder-Using-Verilog-and-Microwind/blob/main/Screenshots/VI_graph.png?raw=true)

### **Tools Used**
- Quartus II: For Verilog coding and RTL generation.
- Microwind: For layout generation and CMOS design.
- DSCH03: For schematic and transistor-level design.


## **Conclusion**
This project successfully demonstrates the design, layout, and simulation of a 4-to-16 decoder. The functionality was verified using simulations, and performance metrics like delay were analyzed. The results highlight the efficiency and correctness of the design.


