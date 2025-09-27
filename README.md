# RISC-V-Tapeout-chip-program-week-1
Building upon the RISC-V learning journey, the focus of Week 1 . it was about the simulation and synthesis of both combinational and sequential circuit . This week was about the  digital design practices essential for progressing toward processor-level implementations.

# Day 1

Day 1 deals with the introduction of basics simulator, design, testbench and the basics of simulation flow with the synthesizer tool i.e yosys. Lab of this day consists of the setting the environment and to do work on iverilog and gtkwave. Yosys is a synthesizer tool which is used to convert the RTL code into netlist. In yosys the design and the library file containing the information of standard cell is given which it generate the corresponding netlist file.

 1. Environment setup

 <img width="1252" height="624" alt="Screenshot 2025-09-26 135442" src="https://github.com/user-attachments/assets/a7ea6a66-2408-4b7b-a82c-3dc7a0878705" />

 2. Iverilog and GTKwave: Done simulation of good_mux
 
 These are invoke using : 
 
 iverilog good_mux.v tb_good_mux.v
 
 ./a.out
 
 gtkwave tb_good_mux.vcd

 
<img width="1267" height="314" alt="Screenshot 2025-09-26 140336" src="https://github.com/user-attachments/assets/0b9d5028-d1ee-41fc-8b84-5d403cfa783e" />

3. Yosys: Yosys is invoke using: 
 
 yosys
 
 read_liberty -lib ../lib/sky130fd_sc_hd__tt_025c_1v80.lib
 
 read_verilog good_mux.v
 
 synth -top good_mux
 
 abc -liberty ../lib/sky130fd_sc_hd__tt_025c_1v80.lib
 
 show
 
 write_verilog -noattr good_mux_net.v

 
![WhatsApp Image 2025-09-27 at 22 31 33_1c07a006](https://github.com/user-attachments/assets/c0fae012-35f3-4880-a83c-83141fc404c9)

Netlist is shown as:

![WhatsApp Image 2025-09-27 at 22 32 42_368a981c](https://github.com/user-attachments/assets/d71c4b27-8f28-476d-af12-0f5637c477a0)

# Day 2: Introduction to .lib

Day 2 deals with the introduction of librsry file and the information it contains. "sky130fd_sc_hd__tt_025c_1v80.lib" this is the library file containing the parameters like process variations, voltage and temperature.

<img width="635" height="993" alt="494755069-2ed22908-7bf6-48b3-86ea-7e813e52bdf7" src="https://github.com/user-attachments/assets/bc026862-634e-45c5-8d5c-6e37936770d1" />

Here, tt stands for typical process, o25c is the temperature with 1v80 as the voltage. In this we also learn about the hierarchical and flat synthesis. here we synthesize the multiple_modules.v file having different submodules.

 ![WhatsApp Image 2025-09-27 at 22 35 55_e685f931](https://github.com/user-attachments/assets/daa2be4b-4a66-4603-a642-2ced1f66791f)

 
![WhatsApp Image 2025-09-27 at 22 36 21_b8f9ad04](https://github.com/user-attachments/assets/e7b3e50a-bbc1-4472-8e7b-4ef721a7a346)

![WhatsApp Image 2025-09-27 at 22 36 30_f097aa51](https://github.com/user-attachments/assets/83f648ac-8988-4d78-9c1f-c67ffe0bf258)

After this, we learned about the basics of flip-flop and the variation in output depending on the synchronous/asynchronous set/reset. Following are the attachments of gtkwave wave of the flip-flop working under different conditions 

![WhatsApp Image 2025-09-27 at 22 39 36_f2951904](https://github.com/user-attachments/assets/e9357baf-231a-453e-9845-9e0eb46355c4)

![WhatsApp Image 2025-09-27 at 22 39 51_5bfa2b13](https://github.com/user-attachments/assets/add9d8da-1e95-43fd-8faa-52ff17b68a84)

![WhatsApp Image 2025-09-27 at 22 40 02_56a53b70](https://github.com/user-attachments/assets/5bf06089-ff40-41ff-9a25-00df0498f7a3)


![WhatsApp Image 2025-09-27 at 22 40 12_d6a494c0](https://github.com/user-attachments/assets/45c2a580-a405-43dc-b9d6-151aa85e3999)

![WhatsApp Image 2025-09-27 at 22 40 18_ea6a1fcf](https://github.com/user-attachments/assets/000488d1-cfd3-48f2-8122-b681d58cd45e)

![WhatsApp Image 2025-09-27 at 22 40 22_a51a9b9c](https://github.com/user-attachments/assets/ecbfedec-31ce-4b28-bd76-0a05914f3d06)

We also look at the special cases of multiply where only the last bit is appending with 0 when multiply by even factor while when there is odd factor there is only replica of same input.


![WhatsApp Image 2025-09-27 at 22 42 44_bcd8ffd1](https://github.com/user-attachments/assets/7f6b4dae-9418-4ded-852e-c2d726d1b28e)

![WhatsApp Image 2025-09-27 at 22 42 48_256e2df2](https://github.com/user-attachments/assets/45c2df98-3a46-4a3b-aeec-81f1a852ba1a)

 
# Day 3 Combinational and Sequential Optimisations

1.Combinational logic optimisation means squeezing the logic to get the most optimized design. It is done through constant propagation and using Boolean logic optimisation. In the opt_check.v files are used. Synthesis involves the following steps:

yosys

read_liberty -lib ../lib/sky130fd_sc_hd__tt_025c_1v80.lib

read_verilog opt_check.v

synth -top opt_check

opt_clean -purge

abc -liberty ../lib/sky130fd_sc_hd__tt_025c_1v80.lib

show

![WhatsApp Image 2025-09-27 at 22 44 08_641834b4](https://github.com/user-attachments/assets/6f5fd726-98e8-4711-9cb8-b6a313367a9e)

![WhatsApp Image 2025-09-27 at 22 44 31_4f600df6](https://github.com/user-attachments/assets/c4fa4f1b-d67f-49de-9869-91fb32b55c3d)

![WhatsApp Image 2025-09-27 at 22 44 55_912586d5](https://github.com/user-attachments/assets/7ac184f4-c683-4d25-9e17-595c4a86aaa8)

2. Sequential logic optimization: It involves two methods: Basic which is a sequential constant propagation and second one is advanced which involves state optimisations, retiming and sequential logic cloning. We done the optimisation of dff_const4.v and dff_const5.v files.

  # dff_const4.v

![WhatsApp Image 2025-09-27 at 22 46 01_cb4024ad](https://github.com/user-attachments/assets/4ec06fba-d8c6-4880-ac03-a5cb045b532b)

![WhatsApp Image 2025-09-27 at 22 46 11_e3968e74](https://github.com/user-attachments/assets/6832a4f4-4a04-4860-8d4c-878202aaa85c)

![WhatsApp Image 2025-09-27 at 22 46 25_bee24a42](https://github.com/user-attachments/assets/8532033d-bae7-4566-846b-731b93a254ee)

    # dff_const5.v

![WhatsApp Image 2025-09-27 at 22 47 00_e24f96b1](https://github.com/user-attachments/assets/27ce5aff-43f1-48c5-958b-dcc64f245c39)

![WhatsApp Image 2025-09-27 at 22 47 22_44c4666a](https://github.com/user-attachments/assets/1f4c1785-fa3b-4dc7-a33e-7fb2597e7f94)

On this day we also learned the sequential optimisation for unused outputs. Here we use the file counter_opt.v, in this all the three bits are used.

![WhatsApp Image 2025-09-27 at 22 48 12_189750f4](https://github.com/user-attachments/assets/3565bb10-0c5e-4874-a67f-92945fd97096)

![WhatsApp Image 2025-09-27 at 22 48 20_474dffc0](https://github.com/user-attachments/assets/fb671c02-6382-436e-b42c-ad1aebbc329c)

code only one bit is used while ither two are unused and the code and the netlist is look like as:

![WhatsApp Image 2025-09-27 at 22 48 55_6bbe7767](https://github.com/user-attachments/assets/2ffaaad7-0fda-43b5-a490-4fd79d0ed3a5)

![WhatsApp Image 2025-09-27 at 22 49 02_c51684c5](https://github.com/user-attachments/assets/70a88769-0c2d-4c29-9c43-7708e847b411)

# Day 4 Introduction to Gate level simulation 

Day 4 deals GLS which means the running the testbench with netlist as design under test (DUT). GLS is used to verify the logical correctness of design after synthesis. It also ensure that the timing is met. Here we also learned about the simulation-synthesis mismatch which occur due to the missing senstivity list, blocking vs non-blocking assignments and non-standard verilog coding. we also done the lab experiment of doing the GLS and checking the simulation-synthesis mismatch. we had done the simulation, synthesis and GLS of ternary_operator_mux.v. For doing the GLS we done the following steps:

iverilog ../my_lib/verilog_model/primitives.v ../my-lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v

./a.out

gtkwave tb_ternary_operator_mux.vcd

![WhatsApp Image 2025-09-27 at 22 50 06_b18d0915](https://github.com/user-attachments/assets/3e7ca5e9-7b65-4ad3-9882-b69d5d2fd54e)

![WhatsApp Image 2025-09-27 at 22 50 20_e89b51cf](https://github.com/user-attachments/assets/79c22a53-b2dd-41a9-8465-d2dfe29bfbe8)

![WhatsApp Image 2025-09-27 at 22 50 29_ce4ff861](https://github.com/user-attachments/assets/4d9cca3b-b4dc-4200-a5e8-d9a9818063f4)

![WhatsApp Image 2025-09-27 at 22 50 36_d3a8b52b](https://github.com/user-attachments/assets/4ed8a742-c14e-44d3-8e52-0f63802bedb7)

We also done the experiment to determine the simulation-synthesis mismatch of file named bad_mux.v

![WhatsApp Image 2025-09-27 at 22 52 24_068058b5](https://github.com/user-attachments/assets/44f81693-a209-47c2-8303-0df2ec559575)

![WhatsApp Image 2025-09-27 at 22 52 42_367611a0](https://github.com/user-attachments/assets/e869fee7-84a9-406c-99f3-37ef34eddaa0)

![WhatsApp Image 2025-09-27 at 22 52 46_f4093274](https://github.com/user-attachments/assets/e9de649a-a594-4232-872b-712c68b6cb0c)

# Day 5  If-Case constructs

1.If statement is used for priority logic. Incomplete "If statement" inferred latches. In this we use "incomp_if2.v" file to check the incompleteness of "if statement".

![WhatsApp Image 2025-09-27 at 22 54 27_a874ee60](https://github.com/user-attachments/assets/bf74aa27-d351-4f66-aad0-96ae14666a69)

![WhatsApp Image 2025-09-27 at 22 54 40_e0f8ca0c](https://github.com/user-attachments/assets/42989407-81ff-4391-84c5-e7b98cc11933)

Case statements executes sequentially where nothing is prioritize. Different caveats of case statement includes the incomplete case statement, partial assignment and the overlapping cases.
  
     # Complete case statement

  ![WhatsApp Image 2025-09-27 at 22 56 10_19293a30](https://github.com/user-attachments/assets/8ec13f50-0271-4a5f-8a0b-7f611dfa6936)

![WhatsApp Image 2025-09-27 at 22 56 22_b39e601d](https://github.com/user-attachments/assets/7e8c66ce-4010-4fe0-8235-1e18a9a0d401)

     # Incomplete case statement

![WhatsApp Image 2025-09-27 at 22 57 17_582de2c2](https://github.com/user-attachments/assets/6c39ff4c-9bc0-443a-b5f2-905a3ff8e01b)

![WhatsApp Image 2025-09-27 at 22 57 29_56a20796](https://github.com/user-attachments/assets/34ac205b-ddcd-4a50-bd7e-ed046ef0310f)

    # Partial case assign statement

 ![WhatsApp Image 2025-09-27 at 22 58 08_328d7ee8](https://github.com/user-attachments/assets/2d9e7c5e-b198-40a2-8584-141232eb5e4d)

![WhatsApp Image 2025-09-27 at 22 58 18_39331185](https://github.com/user-attachments/assets/0a024df8-93fa-4a45-bf3f-213d75490cd2)

    # Bad case statement

![WhatsApp Image 2025-09-27 at 22 59 00_6e18d97f](https://github.com/user-attachments/assets/bb574a33-89bb-44ed-8941-b368865b921b)

![WhatsApp Image 2025-09-27 at 22 59 09_fb44b678](https://github.com/user-attachments/assets/f5f715ec-7c9a-4a7a-b3f9-b27d17b1547c)

In this we generate Demux using "Generate for" looping construct.
 
![WhatsApp Image 2025-09-27 at 23 00 24_10775c75](https://github.com/user-attachments/assets/69514b13-ca35-4c89-9779-fb3a89cec727)

![WhatsApp Image 2025-09-27 at 23 00 34_9261639a](https://github.com/user-attachments/assets/d3476ac0-c70c-4e09-be67-5875afe0026f)

![WhatsApp Image 2025-09-27 at 23 00 42_cd423261](https://github.com/user-attachments/assets/ecb08a7d-4447-4b12-a3b2-156fed5006a8)

![WhatsApp Image 2025-09-27 at 23 00 51_e7ec4e8b](https://github.com/user-attachments/assets/d98a24c3-d5ef-476d-9ba7-6a2ac8c0e87c)

We also done the addition using 8-bit Ripple carry adder using the generate-for loop


![WhatsApp Image 2025-09-27 at 23 02 35_f06e96a0](https://github.com/user-attachments/assets/e84578e7-35f1-439c-9818-49fc1553e849)

![WhatsApp Image 2025-09-27 at 23 02 40_785c0ab3](https://github.com/user-attachments/assets/ace0e93c-8381-4703-b198-fca8795b6b21)

![WhatsApp Image 2025-09-27 at 23 02 59_8e207585](https://github.com/user-attachments/assets/5125e644-becb-4af8-8149-3303477a84f9)

# Acknowledgement

 I'm very thankfull to the team of VSD for this RISC-V tapeout program.
