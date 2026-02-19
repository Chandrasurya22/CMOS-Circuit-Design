# CMOS-Circuit-Design

# NgspiceSky130-Day1-Basics of NMOS Drain Current(Id) vs Drain-to-source Voltage(Vds)

## [Introduction to Circuit Design and Spice Simulations]

### L1 Why do we need SPICE simulations?
Circuit Design: 
1. Through PMOS and NMOS connections we can design the functionalities of the NOT, AND, OR, NOR gates.
2. Basically, in ciruit design, the designing the connections of PMOS and NMOS transistors gives us the required functionality.
<img width="499" height="584" alt="image" src="https://github.com/user-attachments/assets/88914864-6bf2-4f82-b213-c8eaae4d7848" />

Spice Simulation: 
1. Transisitors comes up with Width and Length, The W/L ratio of the transistors will decide the value of current. and these current will decide the waveform.
   <img width="976" height="422" alt="image" src="https://github.com/user-attachments/assets/9981d7a1-850e-47a0-946f-9edd415ad779" />
2. Value of those current --> decides the waveform shape --> this shape in return provides us the information of the delays.
    <img width="674" height="546" alt="image" src="https://github.com/user-attachments/assets/dc8b6583-d457-40fb-8e4f-f05cb142c32e" />

Spice Simulation : If we want to determine the delay, we need to understand how to tune the W/L ratio. This can be achieved by the Spice Simuluation.  
   

**WHy do we need SPICE?**</br>

The clock Tree synthesis, crosstalks, and timing are built on SPICE (Simulation Program with Integrated Circuit Emphasis), without SPICE there won't be delays and if there are no delays, the clock tree, physical design flow, crosstalk won't exist.</br>

Now, from Clock Tree Synthesis,  the below circuit with type 1 and type 2 buffers, which has the below values. </br> 

<img width="1721" height="538" alt="image" src="https://github.com/user-attachments/assets/64d2eeaa-9bb1-4d6c-91f4-ef62f983f947" /> 

Input Slew: Input slew is the speed at which the input voltage transitions, typically measured as the slope of the rising or falling edge of a signal
            Units : voltage per unit time. ( V/ns).  
            >>> In Digital circuits, input slew describes how fast a logic changes from low to high or high to low. 
            
Gate Delay ∝ f(input slew, Output Load) </br>

Delay Table consists of the input slew and output load. The intersection value of the input slew and output load in the table is taken as delay. 
In Reality, Every PMOS, NMOS transisitor different from its nearest transistor. ( this might because, one might be of lower drive strength and other can be higer driver stength. )

Delay tables for both level 1 and level 2 buffers have been shown. These delay information is coming from the spice simulations. 
This is calculated by circuit design and simulation</br>

<img width="1916" height="501" alt="image" src="https://github.com/user-attachments/assets/754805a8-8093-45cc-a49d-dcdff06d89fb" />

The source of the above Delay Tables comes from circuit design using SPICE simulations. SPICE simulations involves characterisation of any CMOS logic.</br>





### L2 Introduction to basic element in circuit design-NMOS

<img width="723" height="618" alt="image" src="https://github.com/user-attachments/assets/50e8ab80-b29d-481f-8536-7b90954105ef" />

#[NMOS Transistor:]
1. 4 Terminal Device
2. Built on P-substrate, it forms N channel as it is NMOS. 
3. Two Isolation Region ( SiO2) ---> this is used to differentiate between adjacent transistors
4. Has heavily doped n+ regions
5. Gate oxide layer, and on top of it there is a Poly-Si gate terminal.
6. G- Gate
7. S- Source
8. D- Drain
9. B - Body ---- It is an important terminal to understand the threshold voltage of this device. Any potential which has been applied on this terminal tunes the threshold voltage.  

**Threshold Voltage**

Threshold Voltage - all the characterisation depends on threshold voltage 

<img width="751" height="502" alt="image" src="https://github.com/user-attachments/assets/16640f34-8bbb-4054-97c0-ffe3205e6cf8" />

--> Vgs = 0 ( giving no voltage at gate ) 

--> Drain, Source, Bulk Connected to Ground ( GND) 

--> Substrate - Source (B-S) and Substrate - Drain (B-D) forms p-n junction diode. 
So both the juctions are 'off' due to 0V bias. 

--> Hence Source drain resistance is high as there is no Connectivity between source and drain. 

Now Applying a small +ve voltage at Gate (Vgs>0) 
Then, Metal plate gets positively charged, as a result of +ve charge it will repel all the +ve charges present in the channel. 
leaving behind the -ve charges 
<img width="947" height="575" alt="image" src="https://github.com/user-attachments/assets/cfc21c82-031f-4583-9412-0741724a95d2" />


Because of this phenomenon, there is an accumulation of -ve charges 
<img width="988" height="562" alt="image" src="https://github.com/user-attachments/assets/8f41fba4-46ce-4670-9fef-ab7363bc3e95" />



### L3 Strong inversion and threshold voltage

1. Along with the Accumation, there is a Formation of Depletion region, whenever applied a positive potential, this region between the source and drain will get depleted of its majority carriers
2. In P-N junction diode --> whenever reverse bias is applied across P-N junction diode there is a formation of depletion region.
   <img width="1436" height="524" alt="image" src="https://github.com/user-attachments/assets/c73831c1-5d3e-4b5a-ad46-a58fcc2d872c" />

3.  Now we will increase the gate voltage, "Vgs" --> As we increase more and more --> more +ve charges repels --> depletion width increases.
4.  We shall increase gate voltage until the point that the portion of p-substrate inverts to n-type material. This phenomon is called Strong Inversion.

    <img width="859" height="592" alt="image" src="https://github.com/user-attachments/assets/138616de-6aa2-4cec-9e57-d2274e05f411" />

5. If we further increase the gate voltage (Vgs), there is no way it repel positive charges, it will attract the negative charges from nearly space source area which is heavily doped with n+ region. It will attract those and channel width increases. 
6. At this moment, there is no change in depletion width.
7. Continuous n-channel formation from S-D, whose conductivity is modulated by "Vgs".
   <img width="647" height="528" alt="image" src="https://github.com/user-attachments/assets/5cfef5f6-ed18-4851-8ef3-d015ef412c0f" />


---> Case 1:  Vsb = 0
The depletion width between the p-n junction ( substrate - source ) will be normal as per specification, as there is no particular potential between substrate and source. 

---> Case 2: Vsb = +ve potential 

The depletion width between the p-n junction ( substrate - Source ) will be more compared to the NMOS with Vsb = 0. 
due to the additional reverse bias. 

<img width="1532" height="666" alt="image" src="https://github.com/user-attachments/assets/f72d0ca8-cc1f-4f60-a65d-dbd430caa824" />


