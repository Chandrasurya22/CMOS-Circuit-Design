# CMOS-Circuit-Design
# CMOS-Circuit-Design-Spice-Simulation-using-Sky130nm-technology

## Table Of Contents
- [NgspiceSky130-Day1-Basics of NMOS Drain Current(Id) vs Drain-to-source Voltage(Vds)](#NgspiceSky130-Day1-Basics-of-NMOS-Drain-Current(Id)-vs-Drain-to-source-Voltage(Vds))
  - [Introduction to Circuit Design and Spice Simulations](#Introduction-to-Circuit-Design-and-Spice-Simulations)
    - [L1 Why do we need SPICE simulations?](#L1-Why-do-we-need-SPICE-simulations?)
    - [L2 Introduction to basic element in circuit design-NMOS](#L2-Introduction-to-basic-element-in-circuit-design-NMOS)
    - [L3 Strong inversion and threshold voltage](#L3-Strong-inversion-and-threshold-voltage)
    - [L4 Threshold voltage with positive substrate potential](#L4-Threshold-voltage-with-positive-substrate-potential)
  - [NMOS resistive region and Saturation region of operation](#NMOS-resistive-region-and-Saturation-region-of-operation)
    - [L1 Resistive region of operation with small drain-source voltage](#L1-Resistive-region-of-operation-with-small-drain-source-voltage)
    - [L2 Drift current theory](#L2-Drift-current-theory)
    - [L3 Drain current model for Linear region of operation](#L3-Drain-current-model-for-Linear-region-of-operation)
    - [L4 SPICE conclusion to resistive operation](#L4-SPICE-conclusion-to-resistive-operation)
    - [L5 Pinch-off region condition](#L5-Pinch-off-region-condition)
    - [L6 Drain current model for saturation region of operation](#L6-Drain-current-model-for-saturation-region-of-operation)
  - [Introduction to SPICE](#Introduction-to-SPICE)
    - [L1 Basic SPICE setup](#L1-Basic-SPICE-setup)
    - [L2 Circuit description in SPICE syntax](#L2-Circuit-description-in-SPICE-syntax)
    - [L3 Define Technology parameters](#L3-Define-Technology-parameters)
    - [L4 First SPICE simulation](#L4-First-SPICE-simulation)
    - [L5 SPICE lab with Sky130 models](#L5-SPICE-lab-with-Sky130-models)
- [NgspiceSky130-Day2-Velocity saturation and basics of CMOS inverter VTC](#NgspiceSky130-Day2-Velocity-saturation-and-basics-of-CMOS-inverter-VTC)
  - [SPICE simulation for lower nodes and velocity saturation effect](#SPICE-simulation-for-lower-nodes-and-velocity-saturation-effect)
    - [L1 SPICE simulation for lower nodes](#L1-SPICE-simulation-for-lower-nodes)
    - [L2 Drain current vs gate voltage for long and short channel device](#L2-Drain-current-vs-gate-voltage-for-long-and-short-channel-device)
    - [L3 Velocity saturation at lower and higher electric fields](#L3-Velocity-saturation-at-lower-and-higher-electric-fields)
    - [L4 Velocity saturation drain current model](#L4-Velocity-saturation-drain-current-model)
    - [L5 Labs Sky130 Id-Vgs](#L5-Labs-Sky130-Id-Vgs)
    - [L6 Labs Sky130 Vt](#L6-Labs-Sky130-Vt)
  - [CMOS voltage transfer characteristics (VTC)](#CMOS-voltage-transfer-characteristics-(VTC))
    - [L1 MOSFET as a switch](#L1-MOSFET-as-a-switch)
    - [L2 Introduction to standard MOS voltage current parameters](#L2-Introduction-to-standard-MOS-voltage-current-parameters)
    - [L3 PMOS/NMOS drain current vs drain voltage](#L3-PMOS/NMOS-drain-current-vs-drain-voltage)
    - [L4 Step1- Convert PMOS gate-source-voltage to Vin](#L4-Step1--Convert-PMOS-gate-source-voltage-to-Vin)
    - [L5 Step2 & Step3- Convert PMOS and NMOS drain-source-voltage to Vout](#L5-Step2-&-Step3--Convert-PMOS-and-NMOS-drain-source-voltage-to-Vout)
    - [L6 Step4- Merge PMOS-NMOS load curves and plot VTC](#L6-Step4--Merge-PMOS-NMOS-load-curves-and-plot-VTC)
- [NgspiceSky130-Day3-CMOS switching threshold and dynamic simulations](#NgspiceSky130-Day3-CMOS-switching-threshold-and-dynamic-simulations)
  - [Voltage transfer characteristics-SPICE simulations](#Voltage-transfer-characteristics-SPICE-simulations)
    - [L1 SPICE deck creation for CMOS inverter](#L1-SPICE-deck-creation-for-CMOS-inverter)
    - [L2 SPICE simulation for CMOS inverter](#L2-SPICE-simulation-for-CMOS-inverter)
    - [L3 Labs Sky130 SPICE simulation for CMOS](#L3-Labs-Sky130-SPICE-simulation-for-CMOS)
  - [Static behaviour evaluation-CMOS inverter robustness-Switching Threshold](#Static-behaviour-evaluation-CMOS-inverter-robustness-Switching-Threshold)
    - [L1 Switching Threshold, Vm](#L1-Switching-Threshold,-Vm)
    - [L2 Analytical expression of Vm as a function of (W/L)n and (W/L)p](#L2-Analytical-expression-of-Vm-as-a-function-of-(W/L)n-and-(W/L)p)
    - [L3 Analytical expression of (W/L)n and (W/L)p as a function of Vm](#L3-Analytical-expression-of-(W/L)n-and-(W/L)p-as-a-function-of-Vm)
    - [L4 Static and Dynamic simulation of CMOS inverter](#L4-Static-and-Dynamic-simulation-of-CMOS-inverter)
    - [L5 Static and Dynamic simulation of CMOS inverter with increased PMOS width](#L5-Static-and-Dynamic-simulation-of-CMOS-inverter-with-increased-PMOS-width)
    - [L6 Applications of CMOS inverter in clock network and STA](#L6-Applications-of-CMOS-inverter-in-clock-network-and-STA)
- [NgspiceSky130-Day4-CMOS Noise Margin robustness evaluation](#NgspiceSky130-Day4-CMOS-Noise-Margin-robustness-evaluation)
  - [Static behaviour evaluation-CMOS inverter robustness-Noise Margin](#Static-behaviour-evaluation-CMOS-inverter-robustness-Noise-Margin)
    - [L1 Introduction to Noise Margin](#L1-Introduction-to-Noise-Margin)
    - [L2 Noise Margin voltage paramters](#L2-Noise-Margin-voltage-paramters)
    - [L3 Noise margin equation and summary](#L3-Noise-margin-equation-and-summary)
    - [L4 Noise margin variation with respect to PMOS width](#L4-Noise-margin-variation-with-respect-to-PMOS-width)
    - [L5 Sky130 Noise margin labs](#L5-Sky130-Noise-margin-labs)
- [NgspiceSky130-Day5-CMOS power supply and device variation robustness evaluation](#NgspiceSky130-Day5-CMOS-power-supply-and-device-variation-robustness-evaluation)
  - [Static behaviour evaluation-CMOS inverter robustness-Power supply variation](#Static-behaviour-evaluation-CMOS-inverter-robustness-Power-supply-variation)
    - [L1 Smart SPICE simulations for power supply variations](#L1-Smart-SPICE-simulations-for-power-supply-variations)
    - [L2 Advantages and disadvantages using low supply voltage](#L2-Advantages-and-disadvantages-using-low-supply-voltage)
    - [L3 Sky130 Supply variation Labs](#L3-Sky130-Supply-variation-Labs)
  - [Static behaviour evaluation-CMOS inverter robustness-Device variation](#Static-behaviour-evaluation-CMOS-inverter-robustness-Device-variation)
    - [L1 Sources of variation - Etching process](#L1-Sources-of-variation---Etching-process)
    - [L2 Sources of variation - Oxide thickness](#L2-Sources-of-variation---Oxide-thickness)
    - [L3 Smart SPICE simulation for device variations](#L3-Smart-SPICE-simulation-for-device-variations)
    - [L4 Conclusion](#L4-Conclusion)
    - [L5 Sky130 device variations labs](#L5-Sky130-device-variations-labs)

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

### Threshold Voltage with positive substrate potential

An important observation: 
So in referring to the above mentioned Case 2 of ( Vsb = +ve value ), Due to the presence of the +ve Vsb, few charges from the channel are pulled towards the source 'S'. 
<img width="511" height="347" alt="image" src="https://github.com/user-attachments/assets/076c02ff-f58a-4500-b9f2-3bca28c7b192" />

This does not happend when you have given the Vsb = 0. 

Due to this the surface inversion will be slower in second case. 

So, in order to overcome the above scenario, we need to increase/ have more>>>Vsb 

--> for Vsb = 0 ; Vgs = Vto ( say) ----> Surface inversion is happening 
--> for Vsb = +++Ve ; Vgs = Vto + V1 ---> There is a surface inversion is happening.   
we need an additional potential for this strong surface inversion to happen. 

 <img width="916" height="490" alt="image" src="https://github.com/user-attachments/assets/2471d2ce-0c2c-47e5-8df1-890e106078a3" />

--> Vto, Fermi Potential, Gamma will comes from the foundary. these models are being fed to spice simulation. The Threshold equation will represent the MOSFET device. 

<img width="452" height="227" alt="image" src="https://github.com/user-attachments/assets/124c3e8b-c681-49de-bc6d-2de9f46bd8f2" />

Once you give the parameters to the SPICE tool, it will derive the threshold voltage, which will represnt the mentioned NMOS. 

<img width="897" height="499" alt="image" src="https://github.com/user-attachments/assets/3f798dd7-e3cf-440f-9463-c4ad501076b9" />


## NMOS Resistive Region and Saturation region of Operation

### 4-L1 Resistive region of operation with small drain-source voltage

Resitive Operation: 

--> What happens at different voltages -- Vgs > Vt
--> If we keep on increasing the Vgs -- Channel width will increase. 
--> This shows that the net Induced charges is propotional to (Vgs-Vt).
<img width="872" height="361" alt="image" src="https://github.com/user-attachments/assets/d587946c-d5fb-4a73-af1b-d9a817d55755" />

--> For the start lets apply a small voltage at Vds ( lets say 0.05V) and keep Vt ( NMOS )= 0.45V. & Vgs = 1V

 <img width="872" height="378" alt="image" src="https://github.com/user-attachments/assets/81175bfe-1a6c-4212-9584-b23cd532c46b" />

--> Source is connected to ground, Drain connected to the Vds. Ideally there will be a voltage graident in the channel, as the source is having zero potential and the drain is having Vds potential. 

--> Voltage is not connstant all over the channel, starts at 0 and ends at Vds. 
<img width="497" height="377" alt="image" src="https://github.com/user-attachments/assets/76196b10-120e-4a34-a49c-9e7753071bbe" />


--> Effective Channel Length is different from the actual channel length. Also, the Effective channel length is much lesser than the original channel length

--> Y - is the width of the transistor. X is the point at which there is V(x) ( voltage across the channel) 

--> Due to the application of the Vds, every point on the channel will have the voltage of the Vgs - V(X). 
On applying Vds, every point on x axis will vary w.r.t to Vgs-V(x), this will decide the current equation.


<img width="1915" height="1020" alt="image" src="https://github.com/user-attachments/assets/3a4c21a2-9a55-471d-805c-730d8e33c6fe" />

### 5-L2 Drift current theory

As we Know the effective channel voltage will vary w.r.t x,

for example 
at x = 0; Vgs = 1v and V(x) = 0. 
Effective channel voltage = Vgs - Vx ==> 1V 

at x = Vds = 0.05V, 
Effective channel voltage = Vgs - Vx ===> 1 - 0.05 = 4.95V 

As you can observer there is a voltage gradient in the channel and the voltage is decreasing (higher to lower voltage) across the channel due to the potential at the drain.
Now if we see the induced chagre equation, it is proportional to the effective channel voltage.</br>

<img width="917" height="555" alt="image" src="https://github.com/user-attachments/assets/c28d1344-6f13-49d2-a6dc-c5875a5b6079" />

Curent is function of the charge present in the channel. 

<img width="918" height="512" alt="image" src="https://github.com/user-attachments/assets/af637962-2e4c-4434-a78c-da67eb2f7a68" />


There are two different current: 
1. Drift current:
      1. Current due to the potential difference.
2. Diffusion Current :
       1. Current due to the difference in the carrier concentration.

Here we are discussion regarding the drift current as there is potential difference between the point x = 0  and at x = Vds. 

<img width="880" height="494" alt="image" src="https://github.com/user-attachments/assets/73dddf66-4fa3-4e77-8c3f-ce61223b09cb" />

==> Drift current: Current due to the potential difference.

Id ( drift current ) = ( velocity of charge carrier )  X  ( available charge ) over channel width 

<img width="894" height="508" alt="image" src="https://github.com/user-attachments/assets/7cff8e42-1c8b-486d-b989-03d81d1b95f0" />

### L3 Drain current model for Linear region of operation

As a result of change in the voltage across the channel length, the velocity will change. 
The velocity is the function of the mobility and elctric field </br>
Mobility is constant for electrons and holes for the charge carriers. 

<img width="880" height="525" alt="image" src="https://github.com/user-attachments/assets/b88372e8-88dd-44dc-86e4-698746eeec74" />

<img width="897" height="522" alt="image" src="https://github.com/user-attachments/assets/22709a80-56f3-43bc-95cf-2579a7d76763" />

Integrating the equation. 

We will integrate the above equation, where limits of dV will be 0 to Vds and limits of dx will be 0 to L.</br>

<img width="897" height="517" alt="image" src="https://github.com/user-attachments/assets/16b3017b-2739-4489-8c0b-b634562fa991" />

Here, Cox, W/L, Vgs, Un and Vt are the 'technology parameters', we will simulate using SPICE and find out the characteristics.</br>

But, here we cannot say that it is in Linear region, since the Drain current is the quadratic function of Vds. We will calculate the Id with the given values.</br>


Drain current equation. 

<img width="939" height="548" alt="image" src="https://github.com/user-attachments/assets/bdf67e28-e844-40bd-a04e-6e1a79ec59cf" />


whenever your Vds <= ( Vgs - Vt ) ---> your MOSFET operates in the "linear region". 
so ( Vds*2 ) / 2 = 0 ( as we are approximating to 0 due to value close to zero ) 

For all Vds <= ( Vgs - Vt ) your device will work in the linear region or resisitive region of operation. 

<img width="877" height="506" alt="image" src="https://github.com/user-attachments/assets/e791014a-9d31-41c2-a688-90f406ca0cc5" />

### L4 SPICE conclusion to resistive operation

We have to see the impact of the Vgs and Vds on the drain current equation. when we try to vary Vgs and Vds, we need to understand how the device behaves for the different voltages of these. </br>

<img width="886" height="530" alt="image" src="https://github.com/user-attachments/assets/89c42fac-0b1f-4cbc-a0fd-0e1243df6837" />

If we consider different values of Vgs, under what condition the device will remain in Linear region depends on (Vgs-Vt) should be greater than Vds.

<img width="875" height="371" alt="image" src="https://github.com/user-attachments/assets/f6511f2c-9cc5-45e0-a4b8-db6112cb2cb1" />


Now the question is how do we calculate Id for different values of the 'Vgs' and at every value fo the Vgs, sweep Vds till ( Vgs - Vt) and still identify the drain current using the Linear equation for Id. 

For that Calculations, we will do the SPICE SIMULATIONS

### L5 Pinch-off region condition

The Drain to source voltage (Vds) is increased now beyond the Vt. 
Channel Voltage = Vgs - Vds 

There is also a Region of operation when Drain-source voltage exceeds the value (Vgs-Vt), the region of operation is called "Saturation Region".

Now awe will increase the Vds gradually to observe the characteristics of the device. 
<img width="918" height="547" alt="image" src="https://github.com/user-attachments/assets/4dc8070a-198a-47e1-802b-f5d43d60d711" />


<img width="920" height="519" alt="image" src="https://github.com/user-attachments/assets/1a2bec2d-5bd3-47d5-a7f6-f3483e4a1eb2" />


When we give Vds = 0.55 V. then the channel voltage = 0.45V 
Out of two points in the channel , one point will have 1V ( > Vt) and other will have 0.45V   ( = Vt) </br> 
The voltage at surface inversion happens is at the Threshold voltage. 

<img width="908" height="532" alt="image" src="https://github.com/user-attachments/assets/de24e007-e4a1-4d02-93ac-6b44ef5c99bd" />

<img width="902" height="513" alt="image" src="https://github.com/user-attachments/assets/d891c8b9-3df2-4aa5-a8b0-2e006de81953" />


Channel getting disappear from the point. This phenomenon of channel getting disappeared is reffered to as Pinch-Off Phenomenon. 
Pinch - Off Phenonmenon == Channel begins to disappear. 

<img width="893" height="474" alt="image" src="https://github.com/user-attachments/assets/19685cb1-d37e-4626-9a41-8b6857a11a0e" />


This means there is still current flow exists, as there is still some potential difference in the channel. But only thing is that the Linearity of the Current wil differ. 

On Further increasing the Vds. 
Channel will get disappeared from the Drain region. But there is some channel present in the source area. This condition is reffered as "Saturation region", when the mosfet is saturated and cannot do anything further.
 
<img width="903" height="493" alt="image" src="https://github.com/user-attachments/assets/75f97006-6946-4c14-939f-896a15f5212e" />

### L6 Drain current model for saturation region of operation

In Saturation Region, Channel Voltage will remain constant as 'Vgs-Vt', It is no more the function of the Vds. 

<img width="890" height="500" alt="image" src="https://github.com/user-attachments/assets/adacfd2e-25d1-4f22-8cd3-e76471eb6fe4" />


Derivation of the Drain current in the Saturation region. 

When you move higher values of the Vds, the channel voltage will remain constant. Overall area will remain constant ( Vgs - Vt ) 
So when we say channel voltage , it the voltage between drain to source. 
We will replace Vds by Vgs - Vt,  

<img width="899" height="525" alt="image" src="https://github.com/user-attachments/assets/74f83312-e7a6-4434-9e60-b1ef7489e009" />

<img width="899" height="511" alt="image" src="https://github.com/user-attachments/assets/c71bacd5-6d36-4a8d-b50b-cb4d43d5250b" />

<img width="911" height="535" alt="image" src="https://github.com/user-attachments/assets/6d622c74-d20c-467b-a28a-08ccf0764f79" />

Looks like Drain current is being the function of all the constants. just mosfet act  like a perfect currrent source. But it is not true. 

<img width="907" height="512" alt="image" src="https://github.com/user-attachments/assets/9951d120-0592-4853-a00b-1fcc64a9c329" />

But there is some dependency on the Vds. 
Drain current is not constant, but slightly increases when you increase the Vds. 

As Vds Increases,, Depletion region at drain increases,, and the Effective Channel length will decreases... 

This is called "Channel Length Modulation".
<img width="933" height="516" alt="image" src="https://github.com/user-attachments/assets/c7c1ee32-e5cb-4a44-8e9d-3fb25dffd9fe" />

This equation, becomes equation for the constant current equation for the mosfet in saturation region. 

<img width="585" height="121" alt="image" src="https://github.com/user-attachments/assets/364100b7-df1a-41a4-9b2b-9900113b8e1f" />


## Introduction to SPICE

### L1 Introduction to SPICE 

We need to feed in the correct value to the engine to generate the values. 
Spice Setup. 

<img width="889" height="513" alt="image" src="https://github.com/user-attachments/assets/6207c01b-85d4-452c-a624-688d36df8488" />


the ones which are highlighted in the yellow are constants. 
These are the technology constants, comes from the foundry. ( 20nm, 180nm) -- every technology nodes will have its unique values.

<img width="904" height="521" alt="image" src="https://github.com/user-attachments/assets/9ac3a327-cd5f-4df2-808e-adcc6febbdfc" />

<img width="913" height="510" alt="image" src="https://github.com/user-attachments/assets/12b24f55-808c-4809-83c0-7a19a61065f9" />

these are ones which you provide to the engine in the form of the model files 

Yellow highlighted onces are the SPICE Model parameters. these needed to be fed correctly to get the correct waveforms. 

SPICE model Parameters + SPICE netlist ---> SPICE Software ---> Waveforms  ( grphs ) 
So, when we feed the SPICE model parameters and SPICE netlist into the SPICE software, we get the device characteristics in terms of Id vs Vds with different values of Vgs.

<img width="910" height="522" alt="image" src="https://github.com/user-attachments/assets/e4862c9b-b6f2-445b-be35-bd512578df04" />

Details of the SPICE netlist : 
**SPICE Netlist**
<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/34294082-989e-4d62-82f0-2ab35d7bb1d5" />



### L2 Circuit description in SPICE Syntax

Write the Syntax for circuits in SPICE netlist. 

Steps: 

**Define Nodes** 

<img width="906" height="503" alt="image" src="https://github.com/user-attachments/assets/6df297aa-0f36-4647-8d92-bfc885dc86da" />

define the nodes, so that we define the componets between the nodes.

<img width="902" height="512" alt="image" src="https://github.com/user-attachments/assets/34d4f19e-f080-4c07-8c01-28477f63b1be" />

<img width="880" height="445" alt="image" src="https://github.com/user-attachments/assets/f8703d13-4d06-49b7-b318-033433eef0bb" />

Convert the nodes into the valid spice netlist 
There is no restrictions for the node names, 

<img width="852" height="376" alt="image" src="https://github.com/user-attachments/assets/172543a4-7ac2-498b-9422-f1ebf2c3d13f" />
Since mosfet has 4 terminals it is between 4 different nodes, similarly resisior is between 2 nodes. 

<img width="853" height="279" alt="image" src="https://github.com/user-attachments/assets/cbf9e092-d186-448e-b458-b6890f541cd1" />
<img width="876" height="261" alt="image" src="https://github.com/user-attachments/assets/30587ec7-d23b-4338-aa03-6bc26ccccbcf" />
<img width="856" height="289" alt="image" src="https://github.com/user-attachments/assets/f04fffd7-d408-4071-a87f-75c8dcff6bc9" />
<img width="859" height="268" alt="image" src="https://github.com/user-attachments/assets/6b97b689-985b-4605-a717-e39a63cacfc0" />
<img width="866" height="280" alt="image" src="https://github.com/user-attachments/assets/23c4770e-22d1-4e86-886a-b8460c628362" />
<img width="849" height="249" alt="image" src="https://github.com/user-attachments/assets/025f8d2d-58ba-4b33-b3f6-9494166b5ea5" />

this is a long channel mosfet.
DGSS -- Drain Gate Source Substrate -- this is the order needed to be followed. 
We need to go component wise, like that define all the components. 
<img width="835" height="299" alt="image" src="https://github.com/user-attachments/assets/d236e680-1c39-48b5-bb49-b6f60e142d02" />

<img width="814" height="246" alt="image" src="https://github.com/user-attachments/assets/53c224e7-4e07-497a-a7c9-420faa4aca64" />
<img width="849" height="279" alt="image" src="https://github.com/user-attachments/assets/566f819b-f6e3-4f5f-b2f5-22d380244c8d" />

This is the netlist which defines 

Once we have defined the netlist, we have to define the TECHNOLOGY File. 

<img width="883" height="411" alt="image" src="https://github.com/user-attachments/assets/849fac6a-818f-442d-bce0-e9bd2705c3f1" />


### L3 Define Technology Paramaeters 

We have a well defined NMOS description. NMOS will have its own models. Nmos, when we will pulgin, SPICE engine will understand, pick up the constants, and  evaluate the threshold voltage and drain current for it. 

<img width="865" height="386" alt="image" src="https://github.com/user-attachments/assets/469c860e-18fe-4bcb-9b23-b1ae0fc398e4" />


Vto, gamma, Kn` , lamda are the constants, when we have those it is very easy to calculate. 
Equation is the model of the Nmos. we need the value of the constants for that specific technology node. 

All these model parameters comes as a PACKAGE

<img width="414" height="414" alt="image" src="https://github.com/user-attachments/assets/027f5110-aedc-42bf-9965-0385649e1a91" />


Engine will evaluate all the models using the constants given in the technology file.

Similarly we will have it for PMOS as well. 

<img width="910" height="524" alt="image" src="https://github.com/user-attachments/assets/f07c4793-9fc3-4d40-953d-597d54248a18" />


Package this .mod file an call it in the netlist at the top. 

<img width="543" height="504" alt="image" src="https://github.com/user-attachments/assets/b6c77f96-f917-421e-ba37-6cbc367445e5" />

Whenever there is line starts with *** it is comments. 
<img width="915" height="521" alt="image" src="https://github.com/user-attachments/assets/cb261cc7-06cb-4ad2-b897-bcd35ed93739" />

Now, we need to sweep the Vgs and Vds for SPICE simulations.</br>

### L4 First SPICE simulation
* Open Virtual box
* Type `cd`
* `https://github.com/kunalg123/sky130CircuitDesignWorkshop.git`

<img width="810" height="162" alt="image" src="https://github.com/user-attachments/assets/41de0445-0d43-4870-bc42-296f2b319625" />


<img width="898" height="278" alt="image" src="https://github.com/user-attachments/assets/0ade77ae-4063-4779-8d27-d40693e052a2" />


<img width="722" height="287" alt="image" src="https://github.com/user-attachments/assets/030c31bc-b2d3-4d2c-b579-b737bf6d3b3f" />

* Inside `sky130_fd_pr` directory we will see cells, models and tech files
* Inside the `cells` files we will see `nfet` and `pfet` cells, these cells we will be using.
* These are the only two cells `nfet' and 'pfet' which are gping to be used in this workshop.

<img width="872" height="217" alt="image" src="https://github.com/user-attachments/assets/a837f2c0-ec80-4e35-838c-5c033b76f0c0" />

Inside `nfet` we will see we will see spice libraries at different corners, we will select one such typical corner.
* In Sky130 technology, it has already pre-seeded / categorized some W and L values for the Nfet, in our designs we have select the W and L values among the mentioned files / sets.
If you take any values outside these sets, it wont simulate it.

<img width="609" height="851" alt="image" src="https://github.com/user-attachments/assets/76feaf5a-a367-4c6c-8b78-efc61b367692" />
Now, inside `models` --> `lib.spice` file. It contains the library files for nfet and pfet for different corners.  mentioning the common files for the nfet and pfet including their corners. 

<img width="896" height="313" alt="image" src="https://github.com/user-attachments/assets/ffdb9d06-27ed-4912-b297-e82ca7b1e339" />
Contains library files for both nfet and pfet 
mentioning the common files for the nfet and pfet including their corners. 
<img width="748" height="893" alt="image" src="https://github.com/user-attachments/assets/2bbf5946-4b08-4528-9dfe-620106db786d" />


<img width="867" height="212" alt="image" src="https://github.com/user-attachments/assets/5e96d502-bac7-4950-9f30-8afb9f264d9d" />

We are including the library file along with specification of the corner.
* Above we see Vdd varying from 0 to 1.8 volts with step size of 0.1V and Vgs sweeping from 0 to 1.8V and with step size of 0.2V

<img width="896" height="732" alt="image" src="https://github.com/user-attachments/assets/5babe0d0-8260-4861-9067-bcebf2cb2842" />

if you want to simulate for different corners, use FF - Fast corner, TT - typical corner, if you want slow fast -- keep sf in the above command.  

and 'sky130_fd_pr__nfet_01v08' is the model name of the nfet which is being used. 
Syntax is : 
DGSB -- Drain gate source bulk. 

Above we see Vdd varying from 0 to 1.8 volts with step size of 0.1V and Vgs sweeping from 0 to 1.8V and with step size of 0.2V



* To run this file, type `ngspice` filename`.spice`

<img width="917" height="716" alt="image" src="https://github.com/user-attachments/assets/231197b8-47b5-4031-b66f-a55aafb16ea6" />


* After the plot command, we wil get ID vs VDs at different values of the Vgs values.
  <img width="1025" height="1000" alt="image" src="https://github.com/user-attachments/assets/13dfd509-bc5c-4f4a-8776-fbb84e2e946f" />

* To check the value of Id for corresponding Vds and Vgs, just left click and see.

### L5 SPICE lab with Sky130 models

If we go inside `models` folder, we will see `all.spice` file. If we open it we will see the scale of Width and Length. </br>

<img width="866" height="306" alt="image" src="https://github.com/user-attachments/assets/2b1b08cd-7951-4f60-9ccc-239a6cfa2b37" />


We can see that W and L values are in microns.</br>
<img width="847" height="732" alt="image" src="https://github.com/user-attachments/assets/dce8cc37-f4bc-493f-9d61-8890ba35bd2a" />





# NgspiceSky130-Day2-Velocity saturation and basics of CMOS inverter VTC

## SPICE simulation for lower nodes and velocity saturation effect

### L1 SPICE simulation for lower nodes

With W = 1.8u, L = 1.2u ( W/L = 1.5 ) 

* X axis plot which overlapping is at Vgs = 0V, as there is Id = 0 , means channel is not turned on.
* All equations are plotted in the curve, while we vary the Vgs, we can plot it manually as well.
  <img width="824" height="459" alt="image" src="https://github.com/user-attachments/assets/4e3d3d84-c9d2-48ce-8d41-b8e7cade4467" />

*   The left area of the curve represents different behaviour of MOSFET compared to the right area
*   In the left region: Drain current is the linear function fo the drain to source voltage.
*   In the Right region: Darin current is no more in linear region. it is in the function of ( 1 + (lamda)Vds)
*   Before reaching the point (Vds = Vgs - Vt) Mosfet is in the resistive, liner region, and beyond it it is in Saturation region.
*   In Satuartion region with slight increase in current due to velocity saturation and below is the Cut off region.Also this case is when the channel length is large.</br>
<img width="914" height="522" alt="image" src="https://github.com/user-attachments/assets/a7967bcb-e06e-4e04-835e-3fa8318aa4d2" />

* Cut off region is the region/ area where your device is in cutt off.  here Vgs < Vt.

* Lets take new Scenario, W = 0.375u, L = 0.25u device ( W/L = 1.5 )
Note: As per the formulas, and the  per curve from last scenario, You will understand that when the W/L ratio is same / constant, you expect that the Ids will be same at any node ( of different W and L ), "BUT IT DOES NOT HAPPEN IN THE SAME WAY"

To prove it, we will run the spice deck with the new W and L values. Keeping rest all the same from the previous. 

<img width="342" height="175" alt="image" src="https://github.com/user-attachments/assets/1f93889f-c80b-47f9-8d60-29ec2dfd17bd" />

Commads which are run : setplot, then dc1, display ( to know what all plots available ) , 

then plot -vdd#branch ( - is given due to the difference in the direction of the conventional current flow vs flow of electrons ) 

### L2 Drain current vs gate voltage for long and short channel device


**Observation 1:**
Let us compare the two simulations we did.

If we see Id values for different Vgs and for Vds=2.5V, there is a quadratic dependency of Id on Vgs. Whereas for short channel device, at Vds=2.5V, the current is increasing linearly due to velocity saturation

There is a quadratic dependence of Id at each Vg 

<img width="892" height="510" alt="image" src="https://github.com/user-attachments/assets/13d3939e-45a5-4e5f-8388-612f07fb7aeb" />

Based on the formula of saturation region, we can infer that the Drain current has quadratic dependence. 
Drain current will quadratically increases with increase in the gate voltage. This is for the long channel MOSFET.  

For Short channel device: 

Anything below 0.25u of length is know as short channel device. 
There is quadratic difference upto a certain Vg, but after that there is a linear dependence. 

Observing for  Drain current vs gate voltage for long and short channel device 
for two different length channel devices. 

<img width="463" height="346" alt="image" src="https://github.com/user-attachments/assets/885dac2a-63a3-4d5c-ad17-780cd59446d2" />

<img width="479" height="394" alt="image" src="https://github.com/user-attachments/assets/8ba93088-34c8-4f1f-87ee-3c944da6f8fe" />

This is one of the effects ( short channel effect )  you will observe while going through the lower nodes. The reasonn this is happening is due to velocity Saturation effect. 

<img width="901" height="509" alt="image" src="https://github.com/user-attachments/assets/00e1ba34-bb52-4cfc-9fbc-f4aa0c3f7f42" />


Now, we keep the Drain to source voltage constant, vary the gate voltage and measure the drain current. This procedure will be applied to both the 1.2u and 0.25u device and observe the graphs. 


Now the Spice deck will remain exactly the same, the only change is in the line mentioned in the below picture. 

<img width="305" height="173" alt="image" src="https://github.com/user-attachments/assets/b05e4dcd-7f09-430e-9b2b-1552187b2e4e" />

<img width="338" height="181" alt="image" src="https://github.com/user-attachments/assets/a54f27a9-33be-4c7c-9af0-f506085afb08" />

Now we will plot graph of Id vs Vgs and sweeping Vds or keeping Vds constant = 2.5V.

This line specify that, now you vary the gate voltage from 0 to 2.5 with increment of the 0.1 
and the VDD ( Vds ) is swept from the 0 to 2.5 with step of 2.5 ( as we want to look into one value of Vds ) 

.dc Vin 0 2.5 0.1 Vdd 0 2.5 2.5  ( what ever there in the left hand side, that will be sweeped or tuned at every value of what you see in the right hand side. ) 

<img width="1917" height="972" alt="image" src="https://github.com/user-attachments/assets/1eae8f1b-9642-4d72-881f-b3788d3f31c7" />

dc2 is of short channel and dc1 is for long channel. 


<img width="1755" height="710" alt="image" src="https://github.com/user-attachments/assets/7cfaeb4d-ca7d-46a8-9945-7f3f75c48d87" />




### L3 Velocity saturation at lower and higher electric fields
For short channel we will see more of a linear behaviour as the Vgs increases. This is due to velocity saturation effect.</br>

<img width="1332" height="592" alt="image" src="https://github.com/user-attachments/assets/95aa490e-3dc0-4875-b74a-836c1ae07486" />
So, for lower node we will have 4 regions of operations: **Cut Off, Linear, Saturation and Velocity Saturation**

**Velocity Saturation**
We know velocity and electric field are related to each other with equation `v=uE`, where v is velocity, E is electric field and u is mobility. Velocity increases linearly with electric field over certain electric field value after which it gets saturated. This is due to scattering at higher fields and mobility decreases. </br>

<img width="973" height="506" alt="image" src="https://github.com/user-attachments/assets/57f60dd0-b579-4e67-962d-03c21c430e49" />

Velocity saturation happens for higher gate-source voltages.</br>

<img width="1011" height="470" alt="image" src="https://github.com/user-attachments/assets/bf8911ed-1708-4c95-adc1-f6816f66a689" />

### L4 Velocity saturation drain current model
<img width="987" height="473" alt="image" src="https://github.com/user-attachments/assets/cbe1cdbb-8b18-4c19-97c6-be3e4244fb34" />

Let us take Vgs-Vt=Vgt because we will be taking Vgs as large values. Current equation we will be using as shown above, For lower values of Vds we will neglect the 'lambda' term.</br>
There is one more technology paramter which is "Vdsat", it is the velocity of gate when the device just enters the Velocity saturation region.</br>
<img width="831" height="212" alt="image" src="https://github.com/user-attachments/assets/2e70d7d1-4891-4488-90e8-93f9b5f1322c" />

<img width="1026" height="536" alt="image" src="https://github.com/user-attachments/assets/724c8f7e-e772-4006-9f39-05d7a8e06b56" />

<img width="1080" height="540" alt="image" src="https://github.com/user-attachments/assets/13ace523-0233-4dd0-802d-d1ab5f026de6" />

<img width="1006" height="538" alt="image" src="https://github.com/user-attachments/assets/2d5432ec-2438-41c5-9b52-2f658a17c006" />

<img width="1331" height="583" alt="image" src="https://github.com/user-attachments/assets/5a5755f0-0723-4aea-8f07-e277cf3fdf18" />

In the above equation, it seems when W is constant and L is lowered then Id should increase, But it is not so practically.</br>

* **Observation 2** - The saturation current for lower nodes is low instead of being high. This is because Velocity saturation tends to saturate the device early so the peak current we see for lower nodes is much lesser than for higher nodes.</vr>
<img width="1370" height="576" alt="image" src="https://github.com/user-attachments/assets/82010154-16a3-4079-a57c-e5a7435b9507" />

### L5 Labs Sky130 Id-Vgs
We will now do simulation for lower nodes. Inside day2 design file.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/2e30ad35-dbfe-42e4-a2c6-1c3e3ffd3d8b" />

<img width="1915" height="1078" alt="image" src="https://github.com/user-attachments/assets/46853bc0-6ac5-4d4e-8c34-133b54530564" />

We can see above, simulation is being done for L=0.15u and W=0.39u.</br>
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/0112c1fb-efa5-4eb2-a5c2-9c34923067ab" />
<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/05b5bf4a-79e4-4b9e-b92d-938707164205" />

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/3455d86b-dd2b-4b41-aad6-4bee2f683440" />

The above plot is Id vs Vds for different values of Vgs. We can see for lower values of Vgs it is showing quadratic behaviour and for higher values of Vgs it is showing Linear behaviour. Now if want to see the peak current for Vgs=1.8V, just 'press' left click on mouse at Vgs=1.8V.</br>

<img width="290" height="22" alt="image" src="https://github.com/user-attachments/assets/83d91519-32f9-4d17-b88a-379635529e9a" />
So we can see it is approximately 198uA.</br>

**Now let us observe Id vs Vgs**
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/38b27e55-94b1-4190-9191-e022f3e3d548" />

Here again we are taking values for L=0.15u and W=0.39u, Keeping Vds constant at 1.8V and sweeping Vgs from 0 to 1.8V with step of 0.1V.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/2c4fd12f-4995-43bc-b1bd-faaa1d6291a7" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/17f7032a-f654-4c22-81e9-acbc1cbe368f" />

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/b490e2f2-76aa-49f1-b37c-e986cb3e4126" />
In the above graph we can see that, due to short channel effect we are seeing a linear behaviour for higher Vgs and Vds being constant.</br>

### L6 Labs Sky130 Vt
Now we will calculate Threshold Voltage Vt for Id vs Vgs curve.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/1e4b97da-884d-4447-b8ae-4d83ff1aef33" />

In the curve we can see that Vt is the value when current increases drastically for small change in Vgs. To calculate we will draw tangent on the curve and see where it touches.</br>

<img width="292" height="30" alt="image" src="https://github.com/user-attachments/assets/dfd6b8ca-308f-425e-97d0-58cb1799fca4" />

It comes at around 0.76V.

## CMOS voltage transfer characteristics (VTC)

### L1 MOSFET as a switch
We will now look at the device parameters from the switch point of view.</br>

<img width="907" height="508" alt="image" src="https://github.com/user-attachments/assets/6bb70912-c36e-4031-bf01-7e05871b28a8" />
The above shows MOSFET as a switch:
* When |Vgs|<Vt, device is OFF and it acts as open switch
* When |Vgs|>Vt, device is ON and it acts as closed switch

<img width="1220" height="685" alt="image" src="https://github.com/user-attachments/assets/48869cbb-daee-4a3b-96a8-bdd0fb45a79f" />

### L2 Introduction to standard MOS voltage current parameters
We are trying to get the equivalent circuit of CMOS when Vin is 'high' and 'low', so that we can get the Voltage Transfer Characteristics (VTC) and therefore calculate the delay of the cell.</br>

* When we take Vin as 'high' and equal to Vdd, PMOS will be OFF and NMOS will be ON
<img width="1292" height="680" alt="image" src="https://github.com/user-attachments/assets/f65a1301-44f9-482e-b8dd-7b5cb3d39e47" />

* When we take Vin as 'low' or equal to '0', PMOS will be ON and NMOS will be OFF.
<img width="1347" height="696" alt="image" src="https://github.com/user-attachments/assets/c15bdbc8-99af-48e0-a23c-726e7e415b66" />

So we can see that when Vin=Vdd there is a direct path that exists between Vss and Vout, the capacitor CL discharges through the resistor.</br>
Similarly when Vin=0 there is a direct path between Vdd and Vout, CL charges.</br>
<img width="1322" height="428" alt="image" src="https://github.com/user-attachments/assets/a4f22e15-1c9a-44cf-bfa2-e27b37557439" />

Let us give the naming convention of the CMOS 

<img width="506" height="618" alt="image" src="https://github.com/user-attachments/assets/7225993f-5a53-4456-9959-3cdf52d77960" />

ALso the current in both the condition is Idsn(drain to source for NMOS) and Idsp(Drain to source for PMOS)
And **Idsp = -Idsn**, both are opposite in direction to each other.

### L3 PMOS/NMOS drain current vs drain voltage
<img width="485" height="677" alt="image" src="https://github.com/user-attachments/assets/f2026254-f2b7-4623-967a-79fbc649a8ea" />

Now if we talk about the curve between Idsn Vs Vdsn and Idsp Vs Vdsp, it is as shown below.

<img width="897" height="432" alt="image" src="https://github.com/user-attachments/assets/2e55422f-9659-4ce7-b6ac-b1fe6d41d1a0" />

### L4 Step1- Convert PMOS gate-source-voltage to Vin
We have seen various internal voltages, but actually in terms of user's perspective we can't see the internal voltages and only see the external Vin and Vout. From these we calculate the VTC and eventually we get to know the delay.</br>

**Now we will see the steps to obtain Voltage Transfer Characteristics(VTC) for static CMOS inverter:**
*Assumption: Let us assume that it is a long channel device with Vdd=2V*
* We will fix the Vgs values as shown below
  <img width="372" height="237" alt="image" src="https://github.com/user-attachments/assets/081d616c-e17f-4741-8a96-0d5eae2b2b9a" />
  
* We know that Vgsp= Vin-Vdd, So we get the above values.So we get Vin = Vgsp+Vdd, we are trying to convert all the voltages as function of Vin and Vout.
* We will try to plot the graph of PMOS in terms of Idsn, the plot will be as shown below. We can see that the corresponding Vin value of Vgsp is being plotted as shown in the above table.

  <img width="871" height="443" alt="image" src="https://github.com/user-attachments/assets/cd415d3f-042b-460e-8314-4bb28d50d663" />

### L5 Step2 & Step3- Convert PMOS and NMOS drain-source-voltage to Vout
Now we be converting the Vdsp and function of output voltage Vin. We know **Vdsp = Vout-Vdd**.</br>
Let us convert Vdsp into Vout. So to get Vout there is a shift of Vdd towards left hand side.</br>

<img width="1333" height="391" alt="image" src="https://github.com/user-attachments/assets/c9709e57-c876-4521-9ff6-88fb68f9927c" />

We can see that whenever Vout=2V that means Vdsp=0V and Vdd=2V (given), then The current is zero and capacitor at the output is discharged. This is true only when PMOS is in combination with NMOS and forms a CMOS inverter.</br>
Let us take another example, when Vout=0V, that means -Vdsp=2V and Vdd=2V, so at every gate voltage of Vin we will see a finite current whenever Vout=0V. As Vout=0V, the capacitor is completely discharged and we need to charge that, so that is the charging current required. So, here we get the load curve for PMOS</br>

<img width="513" height="392" alt="image" src="https://github.com/user-attachments/assets/3a31512c-bd15-4f84-8a43-cb125285ad24" />

Now we will try to get the "load curve" for NMOS transistor from this equations.</br>
<img width="223" height="75" alt="image" src="https://github.com/user-attachments/assets/ede06e12-72e7-4da9-8341-820177ed7b4e" />

It is actually simple as Vgsn = Vin and Vdsn = Vout, directly we can get the graphs.</br>

<img width="410" height="287" alt="image" src="https://github.com/user-attachments/assets/e434b1a5-c734-43c2-9565-19714e01f38e" />
<img width="892" height="380" alt="image" src="https://github.com/user-attachments/assets/143a185e-09e5-4c51-8964-eae5b983c47c" />

### L6 Step4- Merge PMOS-NMOS load curves and plot VTC
We will now merge the above two curves and obtain the voltage transfer characteristics(VTC) for CMOS inverter.

<img width="1340" height="412" alt="image" src="https://github.com/user-attachments/assets/e06060aa-bb37-4abc-a225-7cce4569c224" />
For this we will superimpose both the Load Curves to get the VTC. We are doing this to find out the common point between Vin and Vout of both NMOS and PMOS.</br>

<img width="573" height="361" alt="image" src="https://github.com/user-attachments/assets/60499256-909d-4fad-ba5b-5a5e58d4939d" />

So the  range of Vin and Vout is 0V-2V.</br>

* When Vin = 0V, Vout = 2V; NMOS is Cut Off and PMOS is in Linear region
* When Vin = 0.5V, 1.5V<Vout<2V; NMOS is in Saturation region and PMOS is in Linear region.
* When Vin = 1V, 0.5V<Vout<1.5V; NMOS and PMOS are in Saturation region.
* When Vin = 1.5V, 0<Vout<0.5V; NMOS is Linear region and PMOS is in Saturation region.
* When Vin = 2V, Vout = 0V; NMOS is in linear region and PMOS is Cut Off

<img width="1332" height="687" alt="image" src="https://github.com/user-attachments/assets/e484815f-7533-4c87-a6c3-ca79158ac59e" />

# NgspiceSky130-Day3-CMOS switching threshold and dynamic simulations

## Voltage transfer characteristics-SPICE simulations

### L1 SPICE deck creation for CMOS inverter
We will now simulate the VTC. For that we need to **create the SPICE deck**. It is a connectivity information (Netlist). As there is information about substrate, the circuit is as shown below.Here M1 is PMOS and M2 is NMOS</br>

<img width="546" height="501" alt="image" src="https://github.com/user-attachments/assets/87648d3d-9f23-4e6a-b66a-872306e570f1" />

Next we will write down the **Component Vlaues**, keeping W/L for both NMOS and PMOS same.</br>

<img width="622" height="487" alt="image" src="https://github.com/user-attachments/assets/01bb49d8-39b6-40e1-850f-6a6a95dc5946" />

Next we will assume the **Vin and Vout values**

<img width="585" height="482" alt="image" src="https://github.com/user-attachments/assets/38af526d-c53a-4ff7-91c5-bd804fd572da" />

Next step is to **Identify the Nodes** (Node is the point where two components meet)

<img width="766" height="532" alt="image" src="https://github.com/user-attachments/assets/e7a2d759-0ff9-4c2c-939e-ac4af8840cae" />

**Name the nodes** In model file we will mention like, 2.5V input lies between Vin and 0, similarly Vdd lies between vdd and 0.

<img width="592" height="482" alt="image" src="https://github.com/user-attachments/assets/683acee0-3468-498a-9f94-c804122c5a4b" />

Now let us write the SPICE deck:

<img width="1227" height="585" alt="image" src="https://github.com/user-attachments/assets/1b54b47c-edea-4a16-ac0d-fe40405cd393" />
We know for Mosfet the syntax is DGSS(Drain gate source and substrate).

### L2 SPICE simulation for CMOS inverter
<img width="1197" height="582" alt="image" src="https://github.com/user-attachments/assets/6d58c77a-50fe-4eab-9891-287d7a98ae44" />
<img width="1192" height="553" alt="image" src="https://github.com/user-attachments/assets/a06f6d8e-c074-4aa9-9946-6056ed71f927" />
<img width="1280" height="592" alt="image" src="https://github.com/user-attachments/assets/f4e7acd7-6158-432b-8003-b2c74656f9b0" />

Next comes the **Simulation Commands**</br>
Here we will be sweeping the gate input voltage from 0 to 2.5V with steps of 0.05. We need to find the VTC, for this only we will be sweeping the input voltage and measuring the output voltage.</br>
Final step is to describe the **Model files**, all the information about the technological parameteres is given inside the model files.</br>

<img width="1223" height="565" alt="image" src="https://github.com/user-attachments/assets/1bd6f151-618b-4612-82fd-6b43f7eec459" />

Now we will do the SPICE simulation for Wn=Wp=0.375u, Ln=Lp=0.25u, Wn/ln=Wp/Lp=1.5. Below is the VTC we get for the above netlist.</br>

<img width="743" height="567" alt="image" src="https://github.com/user-attachments/assets/91c4ab55-57f1-45ab-826b-b9a9631647ee" />

Next we will get the VTC for Wn= 0.375u, Wp= 0.9375u, Ln,p=0.25u; Wn/Ln=1.5, Wp/Lp=2.5  (PMOS width is 2.5 times more than NMOS)

<img width="741" height="572" alt="image" src="https://github.com/user-attachments/assets/5d83f191-3962-4e25-99b3-aa5d3f520d92" />

If we observe the previous graph is left shifted slightly. This happens because NMOS is more stronger than PMOS in previous graph.</br>

### L3 Labs Sky130 SPICE simulation for CMOS
We now get the VTC characteristics

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/3e6c8b58-05e8-4c43-94a8-e1f8323a9e00" />
We are using both pfet and nfet for CMOS inverter. We can see that W/L ratio of pmos is 2.33 times greater than that of nmos. And we will be sweeping Vin from 0 to 1.8V with step isze of 0.01V and plotting the Vout.</br>

<img width="1913" height="1078" alt="image" src="https://github.com/user-attachments/assets/a9aa02e7-a3f0-4485-9b07-129fd8260d03" />
To get the plot type `ngspice` and `plot out vs in`.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/2b2cd0ab-86fa-43cb-aae5-6192e7c52c10" />

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/e71074c8-50af-44c1-9316-790007b9394e" />

Now we need to know the Switching Threshold from this graph, it is the point when Vin=Vout.</br>
To zoom in the curve; press righ mouse button + hold it.</br>

<img width="1918" height="1076" alt="image" src="https://github.com/user-attachments/assets/f23c8b99-6ef4-49e3-860b-2e0c324f4320" />
So switching threshold for W/L=2.3 is around 0.876V</br>

<img width="280" height="30" alt="image" src="https://github.com/user-attachments/assets/816fa465-de21-4d8d-bff4-fb79ab059723" />

We will now see the transient analysis:</br>
For that we will go inside the tansient SPICE file for day3</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/fe3e84fa-8511-4f02-917e-570de93216d9" />
We can see that it is for typical corner as before and the W/L is also same. But now we taking transient pulse from 0v to 1V with shift of 0 with rise time and fall time being 0.1ns and 0.1ns respectively, pulse width of 2ns and total time period of 4ns. Let us run this.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/93a365ad-7eff-4172-921b-d0301c2978f7" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/786bea0f-e506-4475-b099-575545bd0685" />

So for rise delay and fall delay, we need to consider 50% of output curve i.e. at 0.9V; out-in.</br>
<img width="305" height="67" alt="image" src="https://github.com/user-attachments/assets/9e8f888e-74a1-465c-8cb5-71ee3302b0f7" />

Therefore **Rise delay = 2.482ns-2.15ns = 0.333ns**

For fall delay, consider while falling.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/4c675f5c-cef5-4f78-8692-67398bbf94eb" />
<img width="315" height="71" alt="image" src="https://github.com/user-attachments/assets/73197af2-d7b5-4545-a2b6-aebde88f7f20" />
Therefore **Fall Delay = 4.334ns-4.050ns = 0.285ns**

## Static behaviour evaluation-CMOS inverter robustness-Switching Threshold

### L1 Switching Threshold, Vm
Let us compare the two different CMOS inverters with different W/L ratios of PMOS and NMOS, we can see that the shape of the VTC is same in both the cases only the switching threshold is different. This shows the robustnesss of CMOS inverter.</br>

<img width="1243" height="578" alt="image" src="https://github.com/user-attachments/assets/c246dc3c-6686-4d8f-b8a5-74136a9323de" />
Let us find out the Switching threshold, Vm in both the cases by drawing a 45 degree line.</br>

So, in first case Vm comes out to be somewhere around 0.9V and in second case Vm=1.2V.</br>
<img width="1168" height="417" alt="image" src="https://github.com/user-attachments/assets/7b300b9a-c5ee-4a11-ab44-6bc6027f8b63" />

This is the area where PMOS and NMOS both are in saturation region. Current flows from both the transistor, it is actually a dangerous situation.

<img width="1083" height="462" alt="image" src="https://github.com/user-attachments/assets/5b52f85c-c43e-4b4f-b38f-e51e8fe28170" />

### L2 Analytical expression of Vm as a function of (W/L)n and (W/L)p
We will now calculate the value of Vm w.r.t the NMOS and PMOS width and length. </br>
<img width="553" height="367" alt="image" src="https://github.com/user-attachments/assets/6c11d77c-26a3-46e5-bf6c-349740e6eb00" />
<img width="860" height="53" alt="image" src="https://github.com/user-attachments/assets/b8533cc5-176d-4cb7-97c3-7d6ad5f4ec88" />
<img width="557" height="148" alt="image" src="https://github.com/user-attachments/assets/aacac08b-2543-4f88-8ddb-ce58cad2b763" />

### L3 Analytical expression of (W/L)n and (W/L)p as a function of Vm
Now here we will calculate the value of W/L for PMOS and NMOS when Vm is given.</br>
We have to move in reverse fashion, as we need to calculate W/L ratio of PMOS and NMOS such that Switching threshold is exatly half of the power supply Vdd = 2.5V, therefore required Vm = 1.25V.</br>
We will start from the current equation itself i.e. **Idsn = -Idsp**

<img width="962" height="362" alt="image" src="https://github.com/user-attachments/assets/4abd767b-176b-42c2-9e2e-bdf52323fed2" />
Expanding Kp and Kn (Gain factor) </br>
<img width="517" height="92" alt="image" src="https://github.com/user-attachments/assets/950f6372-d1d7-4c18-8cfd-5b1f35cdfce5" />
<img width="517" height="92" alt="image" src="https://github.com/user-attachments/assets/a532b030-2296-4ff8-981d-2ab29cd88dea" />

Now here on the RHS all are constants and we will get the values from the model files except Vm, If we know Vm then we can get the W/L ratios.</br>
So now this will allow us to find out for what value of W/L ratio of PMOS will be greater than NMOS based on values of Vm.</br>
We will now see the behaviour of CMOS for below difference in W/L ratios of PMOS and NMOS.</br>

<img width="301" height="233" alt="image" src="https://github.com/user-attachments/assets/8534791b-2793-4986-bdad-4a2ef6bde1fe" />

### L4 Static and Dynamic simulation of CMOS inverter
* For (W/L)n = (W/L)p = 1.5</br>
  <img width="750" height="567" alt="image" src="https://github.com/user-attachments/assets/1c8f3e81-2023-429d-9a9e-b80e35d3ad09" />

  We can also calculate the "Rise Delay" and "Fall Delay" by using the transient analysis, just like we did earlier.</br>
  <img width="1256" height="512" alt="image" src="https://github.com/user-attachments/assets/836bb013-63a3-44aa-b0d5-d640359c35f7" />

### L5 Static and Dynamic simulation of CMOS inverter with increased PMOS width
We will be doing the SPICE simulations for increased width of PMOS transistors and compare the results.</br>
* (W/L)p = 2(W/L)n</br>
  <img width="1181" height="507" alt="image" src="https://github.com/user-attachments/assets/7333b09a-2e41-40b2-881e-373214b16c5b" />

We can see that the Vm is now increased as the PMOS has become more stronger and it needs more current to charge the output load capacitor.</br>
* (W/L)p = 3(W/L)n</br>
  <img width="1197" height="507" alt="image" src="https://github.com/user-attachments/assets/f3bea4a2-8853-4330-8886-86e6ab224069" />

<img width="1241" height="512" alt="image" src="https://github.com/user-attachments/assets/abf77cdf-93df-45b2-8373-b9d526a1c8e6" />
<img width="1207" height="512" alt="image" src="https://github.com/user-attachments/assets/978a4960-3442-4ba5-bd1b-e8f336f8812a" />

*Note: Rise delay decreases with increase in PMOS width, this shows the time required to charge the output capacitor decreases significantly this is because we have a bigger area.* </br>

### L6 Applications of CMOS inverter in clock network and STA
The final data set we got from above experiment is shown below:

<img width="692" height="236" alt="image" src="https://github.com/user-attachments/assets/0359ac26-996d-423d-bd27-99e08b6dddaa" />

There are some conclusions we draw from this experiment: </br>
* During fabrication, there can be slight variation in sizes of PMOS and NMOS from the required one, but the robustness of CMOS inverter is such that, there is not much difference in the Vm with change in sizes.
* When (W/L)p = 2(W/L)n, we see that RISE-FALL delay are approximately equal, if we simulate then we can get the ratio factor such that the Rise delay and fall delay are equal to each other. This shows "Symmetry" of CMOS inverter.
  
  *This is a typical characteristic of Clock Inverter/buffer where we want the rise delay and fall delay to be equal.* </br>
  <img width="1110" height="653" alt="image" src="https://github.com/user-attachments/assets/30d33241-5e2f-4389-9a80-cd8d2ad5baaf" />
* Other types of cells can be used according to the data path requirement

# NgspiceSky130-Day4-CMOS Noise Margin robustness evaluation

## Static behaviour evaluation-CMOS inverter robustness-Noise Margin

### L1 Introduction to Noise Margin
Now we will learn CMOS inverter's robustness towards the Noise Margin. Also we see the Noise margin evaluation for CMOS inverter. </br>
**Noise Margin**: It is a measure of how much unwanted electrical noise a logic circuit can tolerate on its input without producing an incorrect output. </br>

For example if we consider an ideal Inverter, for inputs 0/1 it gives output as 1/0. The slope of switch is infinite. </br>

<img width="557" height="451" alt="image" src="https://github.com/user-attachments/assets/2465a4e2-199d-4698-aa7d-58f0b42f0c6f" />

But practically the slope won't be infinite, due to presence of resistances and capacitances there will be delay. Therefore we will get a finite slope </br>

<img width="368" height="316" alt="image" src="https://github.com/user-attachments/assets/f8f2f3f3-dc21-45eb-90b7-c9f2fdb8ef94" />

We will now see that whenever the input is between 0 to VIL(input low voltage); the output will be VOH(output high). </br>
And whenever the input is between VIH(input high voltage) and Vdd; output will be VOL(output low voltage). </br>
<img width="405" height="342" alt="image" src="https://github.com/user-attachments/assets/8e3c22bf-b012-4a75-a08d-910511ed2980" />

### L2 Noise Margin voltage paramters
Considering the more practical scenarios and non idealities of an inverter, the curve we get is as shown below. So here the when the 0<Vin<VIL --> output is VOH<Vout<Vdd ; and when the input is VOL<Vin<Vdd --> output is 0<Vout<VOL. Also **VOL<VOH<Vdd** as VOH will be output high for the next inverter which will be connected and **0<VOL<VIL** as it will be the output low for the next inverter. </br>

Also, the slope is approximately -1, as for increase in input, output is reducing. </br>

<img width="356" height="337" alt="image" src="https://github.com/user-attachments/assets/d848d4c0-de9b-4b6b-8c6a-f3006bae557c" />

### L3 Noise margin equation and summary
Now we will calculate the noise margin equation, for that we will plot the voltages on the same scale.</br>

<img width="733" height="443" alt="image" src="https://github.com/user-attachments/assets/c25a3266-d8f3-4e16-8afa-298756b3a59d" />
In the above scale: </br>
* **Noise amrgin High NH** - value between VIH and VOH. </br>
* **Noise Margin Low NL** - value between VIL and VOL. </br>

So, any value which lies in between noise margins is considered either 1/0 and considered to be tolerable. Apart from this region the value is "Undefined" and the logic level can swing between 'high' and 'low'.

<img width="783" height="423" alt="image" src="https://github.com/user-attachments/assets/80791538-0e36-46a8-9bf1-043e740dd778" />

<img width="822" height="481" alt="image" src="https://github.com/user-attachments/assets/6443e129-644a-4d0d-a4c4-0439ba4165de" />

### L4 Noise margin variation with respect to PMOS width
We will evaluate the noise margin depending upon the PMOS width and ultimately prove that how CMOS inverter is robust to the noise margins.</br>
First, we will find the points where the slope = -1 and extend the lines towards x-y axis.</br>

<img width="1207" height="542" alt="image" src="https://github.com/user-attachments/assets/5ab8cb26-4ab7-4e77-9a04-be82cfcdac12" />
The larger the Noise margin, stronger is CMOS inverter and immune to Noises.</br>

<img width="1175" height="523" alt="image" src="https://github.com/user-attachments/assets/98daed0b-5528-4d72-8a99-06806511d1b8" />
<img width="1197" height="503" alt="image" src="https://github.com/user-attachments/assets/89b5f850-df64-4e6e-abcb-366cc3755d13" />
<img width="1203" height="517" alt="image" src="https://github.com/user-attachments/assets/13199ec4-704c-4812-aba2-38257330e40b" />

For (W/L)p=4(W/L)p and (W/L)p=5(W/L)p noise margins are same, so even if we increase the widths further noise margin will be static. 

<img width="677" height="226" alt="image" src="https://github.com/user-attachments/assets/fca7bcac-471c-4114-8c64-4b97cba1f5b0" />

Here also we can verify the robustness of CMOS inverter. </br>

Also we come to know the ranges for "Digital design" and "Analog design" in the CMOS inverter.</br>

<img width="741" height="546" alt="image" src="https://github.com/user-attachments/assets/3e9a0cf6-a232-4ff2-ad4c-214b03803af3" />
<img width="772" height="542" alt="image" src="https://github.com/user-attachments/assets/56c5c94d-b59f-456c-ba92-b22fab03b6d9" />

### L5 Sky130 Noise margin labs
We will now plot Noise margins

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/af440785-3266-41ad-97ed-dd819824aaa5" />
<img width="1918" height="1077" alt="image" src="https://github.com/user-attachments/assets/58aba228-174c-453c-90df-e81aeab49d53" />

We are taking the W/L ratios of PMOS to NMOS as 2.77 and sweeping the Vin from 0 to 1.8V with stepsize of 0.01V.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/7e8e9139-43f7-4aa7-9737-9e7e378d443b" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/bc470f7d-f493-47c5-89e9-dfbad4e053bb" />
<img width="278" height="60" alt="image" src="https://github.com/user-attachments/assets/501565f8-b944-4af8-854b-a9f1eded062b" />

We will take the point where the slope is -1 ; x axis will give VIL and VIH, whereas y axis will give VOH and VOL.

**Noise margin NH = VOH - VIH = 1.70952-0.98778 = 0.72** </br>
**Noise margin NL = VIL - VOL = 0.7733-0.09523 = 0.67807** </br>

# NgspiceSky130-Day5-CMOS power supply and device variation robustness evaluation

## Static behaviour evaluation-CMOS inverter robustness-Power supply variation

### L1 Smart SPICE simulations for power supply variations
While evaluating the robustness of CMOS inverter another factor is **Power Supply Scaling**. On reducing the gate length, the operating power is also reduced. On power scaling the Cmos characteristics should not change.</br>

We will check by simulation, taking two cases.

<img width="1172" height="328" alt="image" src="https://github.com/user-attachments/assets/03dcd0b9-4dd3-4762-83b2-9cbb882e7bc3" />
<img width="723" height="442" alt="image" src="https://github.com/user-attachments/assets/e403056b-c4bb-4b18-a67c-baf5b02842ab" />
<img width="717" height="436" alt="image" src="https://github.com/user-attachments/assets/f357c6d2-fa02-43bc-bf51-184494cf8858" />
<img width="421" height="171" alt="image" src="https://github.com/user-attachments/assets/25f4e021-6818-4e30-85d9-cf300b35bd03" />

We will now plot the VTC charactersitics for Vdd= 2.5V, 2V, 1.5V, 1V, 0.5V;

<img width="742" height="568" alt="image" src="https://github.com/user-attachments/assets/87cf496c-6386-4374-9e92-1a6ef71959c1" />

### L2 Advantages and disadvantages using low supply voltage
We will now analyse the curves we got in after the simulation and see what are the advantages and disadvantages using low supply voltage.</br>
The first factor is to check the "Gain" for all the supply voltages. "Gain Factor" is change in the output voltage divided by change in the input voltage.

<img width="968" height="516" alt="image" src="https://github.com/user-attachments/assets/dd11da87-d570-4fe1-9439-bd449e39af6a" />

<img width="976" height="547" alt="image" src="https://github.com/user-attachments/assets/102b9c1b-82ce-4d72-bc7e-fb502591c636" />

There is energy lowering for low supply voltage.

<img width="1000" height="526" alt="image" src="https://github.com/user-attachments/assets/f9a05a5f-40c0-4bad-be1f-3cd16f1445f4" />
<img width="927" height="527" alt="image" src="https://github.com/user-attachments/assets/b96be82f-5993-4fd1-9cc2-c0756dc212df" />

* Advantages of low supply voltage
  
<img width="722" height="212" alt="image" src="https://github.com/user-attachments/assets/ab3ef568-d3f7-44cb-a6c5-6524ba5b72ec" />

* Disadvantages of low supply voltage
  Due to low supply voltage, the charging and discharging of load capacitor becomes very slow, due to this the Both rise delay and fall delay will increase and lead to a performance impact.

### L3 Sky130 Supply variation Labs
We will calculate the supply variation.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/94a3c1ba-3139-4838-b302-2320ce3f643e" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/56419121-44bb-4f73-9084-06b1503b6544" />

The initial supply voltage is 1.8V and we are reducing it with the step of 0.2V, so there will be 6 iterations.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/af291d32-1484-4d6b-8291-dabc5b70df65" />
We will calculte the Gain: </br>

* **Vdd=1.8V** </br>

  <img width="292" height="61" alt="image" src="https://github.com/user-attachments/assets/0f2c56cc-5fb4-4c1e-9e49-0e7ee75b964b" />

  |Gain| = 7.6229 </br>

* **Vdd=0.8V**

  <img width="267" height="52" alt="image" src="https://github.com/user-attachments/assets/112695f4-b69a-4c76-bd41-a066a08ac6b7" />

  |Gain| = 9.3844 </br>

## Static behaviour evaluation-CMOS inverter robustness-Device variation

### L1 Sources of variation - Etching process
We will see the sources of variation of VTC characteristics in a CMOS inverter.</br>
First is **Etching Process** </br>
If we see a single inverter layout, we will see the length of gate, the width(common area between polysilicon and diffusion). Due to etching process there can be a variation in length and width of CMOS.

<img width="1208" height="580" alt="Screenshot 2025-10-03 203231" src="https://github.com/user-attachments/assets/f4496266-b2a9-4e21-bb84-54e6519478e4" />

Now considering the inverter chain, the variation can differ with different inverter.

<img width="1288" height="652" alt="Screenshot 2025-10-03 203314" src="https://github.com/user-attachments/assets/a326d12c-e0b7-4daa-bf13-311ccaa8e476" />
<img width="1121" height="618" alt="Screenshot 2025-10-03 203404" src="https://github.com/user-attachments/assets/8683fe6c-a634-4720-98d4-8ef619ab52b1" />

The variation is more at the edges or sides than at the center.

<img width="1324" height="621" alt="Screenshot 2025-10-03 203542" src="https://github.com/user-attachments/assets/998d8d7c-941f-4643-a768-13896c578018" />

Therefore the variation in L and W can change the drain current of CMOS inverter.

<img width="926" height="483" alt="Screenshot 2025-10-03 203633" src="https://github.com/user-attachments/assets/b1c7130a-de89-4cf1-ab2e-064702878082" />

### L2 Sources of variation - Oxide thickness
Another source of variation is **Oxide Thickness*</br>
Let us consider the cross-sectional view of CMOS inverter. We will see the oxide under polysilicon gate, while fabricating the thickness can vary.</br>

<img width="1318" height="561" alt="Screenshot 2025-10-03 203747" src="https://github.com/user-attachments/assets/25b705ca-1d73-4127-a9bc-a69e2af0c8c2" />
<img width="826" height="377" alt="Screenshot 2025-10-03 203848" src="https://github.com/user-attachments/assets/df455509-4718-4074-9eda-bb314e6462c0" />

There is a difference between ideal thickness and actual thickness.

<img width="1205" height="597" alt="Screenshot 2025-10-03 203924" src="https://github.com/user-attachments/assets/a802cce3-df91-4e80-9b34-d2f931de9f8d" />

We know **Cox=Eox/tox**, therefore change in tox can actually change the drain current.

<img width="1162" height="461" alt="Screenshot 2025-10-03 204044" src="https://github.com/user-attachments/assets/d06ee6da-3467-41cb-8a0e-280b15faae56" />

### L3 Smart SPICE simulation for device variations
Now we will be doing the SPICE simulation for device variations, and prove the robustness of CMOS inverter inspite of different extreme conditions.</br>
We will see the characteristics for Strong PMOS and week NMOS, this means PMOS width is wider and it has least resistance. Also for weak PMOS and strong PMOS, that means the width of NMOS is more than PMOS and it has least resitance.</br>

<img width="1148" height="339" alt="Screenshot 2025-10-03 224857" src="https://github.com/user-attachments/assets/398d01a6-ffc4-4a10-86a8-3907d3214b69" />
<img width="594" height="436" alt="Screenshot 2025-10-03 224935" src="https://github.com/user-attachments/assets/41b1f2f6-c4ba-4c71-a8e6-d1fc8e3b4844" />
<img width="695" height="398" alt="Screenshot 2025-10-03 224949" src="https://github.com/user-attachments/assets/9314e15f-c027-47ba-b34e-f35d886e5aff" />
<img width="726" height="321" alt="Screenshot 2025-10-03 225121" src="https://github.com/user-attachments/assets/280f196e-1bde-417a-9955-7a0f2029ee39" />
<img width="753" height="567" alt="Screenshot 2025-10-03 225153" src="https://github.com/user-attachments/assets/33e8fc0e-5220-4dc4-8da9-4c8dd5406e02" />

### L4 Conclusion
We will draw some conclusions from the characteristics we got.

<img width="994" height="537" alt="Screenshot 2025-10-03 231012" src="https://github.com/user-attachments/assets/aec473f9-00f5-4028-b122-fa2922affcb3" />

* The Switching threshold 'Vm' is shifted right in case of strong PMOS and shifted left in case of Strong NMOS. </br>

<img width="1006" height="541" alt="Screenshot 2025-10-03 231027" src="https://github.com/user-attachments/assets/38851b7b-ec82-4400-93d8-c3c651d51ae9" />

* THere not much variation in NOise Margins in both the extreme cases, that means it behaves as a robust inverter in both the cases.</br>

<img width="519" height="169" alt="Screenshot 2025-10-03 231046" src="https://github.com/user-attachments/assets/edd63a58-b8bb-462e-84e5-b8c977d4a4d2" />

### L5 Sky130 device variations labs
We will now do the SPICE simulations for the device variations</br>

<img width="1912" height="1079" alt="Screenshot 2025-10-03 231604" src="https://github.com/user-attachments/assets/5b26708d-6351-4aa8-b2d2-758a174a6f8b" />
<img width="1919" height="1079" alt="Screenshot 2025-10-03 231715" src="https://github.com/user-attachments/assets/518ac3f8-9460-49ab-943e-e09cc37ca4ac" />

We can see that the width of PMOS is quite large than that of NMOS. SO it is clearly strong PMOS and weak NMOS case. The Vm will be right shifted.</br>

<img width="1919" height="1079" alt="Screenshot 2025-10-03 231914" src="https://github.com/user-attachments/assets/ef15e759-7036-445a-b5b1-53b0df38050a" />

<img width="1919" height="1079" alt="Screenshot 2025-10-03 232247" src="https://github.com/user-attachments/assets/841f9eea-395a-4213-93c5-8e5a06de59f0" />


































































  

























































  
