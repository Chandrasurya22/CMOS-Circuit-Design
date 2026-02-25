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
For Short Channel, we will see the sweep from Quadratic to Linear Behaviour as the Vgs increases. It says that the drain current is the quadratic function for the lower values of the Vgs and Linear function for higher values of Vgs. 

<img width="903" height="429" alt="image" src="https://github.com/user-attachments/assets/0e83c1b8-2ab1-46e4-806d-a3e35f6a59cc" />

So, for lower node we will have 4 regions of operations: **Cut Off, Linear, Saturation and Velocity Saturation**

**Velocity Saturation**
* As We know Velocity = mobility * electric field
* At lower fields, the velocity tends to be Linear function, and at the higher fields the velocity tends to become constant. Reason is due to the Scattering effect.
* Velocity saturation happens for higher gate-source voltages

At Lower fields: 
<img width="681" height="255" alt="image" src="https://github.com/user-attachments/assets/cc66ff9b-09b5-4a37-9e48-eb080c45e12f" />

At Higher Fields : 
<img width="685" height="242" alt="image" src="https://github.com/user-attachments/assets/a22c9536-a4b7-4644-a8ba-da2bd4193804" />

* Velocity is the linear function for the E <= Ec ( Ec ---Crictical electric field )
* Velocity is constant for the E >= Ec
  <img width="386" height="93" alt="image" src="https://github.com/user-attachments/assets/b128f57a-6415-4eb1-ab7b-1a90aca4978e" />
<img width="284" height="53" alt="image" src="https://github.com/user-attachments/assets/6bac0479-7df9-4973-b1a7-a7fdba65d3e0" />

For continutity we will keep E = Ec, which brings us to the below equation 

<img width="399" height="121" alt="image" src="https://github.com/user-attachments/assets/b97d1b75-c104-4405-b38d-ba530c4b90f5" />

Now we are re-deriving the drain current using the below boundary condition :  
<img width="885" height="445" alt="image" src="https://github.com/user-attachments/assets/45842a3d-3a94-4168-b547-754f45447379" />
<img width="337" height="153" alt="image" src="https://github.com/user-attachments/assets/a71d4842-b02a-484c-8e95-ee533ff2e591" />

As this model became complex, we are coming up with the simplified one. 

**Operation modes:** 

<img width="673" height="377" alt="image" src="https://github.com/user-attachments/assets/825aee06-c510-49fb-b438-13994eedd03f" />

### L4 Velocity saturation drain current model

<img width="844" height="471" alt="image" src="https://github.com/user-attachments/assets/c76a68ce-34a3-4506-985c-38f0073ea6e0" />

For Example If Vgt = Minimum value, that implies Vgs - Vt is minimum, that is Vds is at Highest, we are implying to the Saturation region.  
<img width="738" height="405" alt="image" src="https://github.com/user-attachments/assets/532c27ac-45d5-4bbb-8688-28c0af72af6b" />


Now Vds = minimum Values, that implies, smaller values of the Vds the device enters into resistive or linear region of operation. 

<img width="751" height="398" alt="image" src="https://github.com/user-attachments/assets/1ed3b4c7-4b1b-48a5-bb6a-9567711112cd" />

As the Vds is minimum, (1+Lamda(Vds)) will get neglected for its lower value.  will become almost one. 


Now Vdsat = minimum value, it will be applicable for short channel devices only. 

<img width="864" height="496" alt="image" src="https://github.com/user-attachments/assets/1533e4d1-2247-4cb9-b467-d548fc850fb9" />

In the above equation, it seems when W is constant and L is lowered then Id should increase, But it is not so practically.



**Observation 2** 

Velocity Saturation causes your device to saturate early. so the peak current we see for lower nodes is much lesser than for higher nodes. Peak current between higher device and lower device is different. For the same W/L ration of the MOSFET the peak current differs. 

<img width="900" height="515" alt="image" src="https://github.com/user-attachments/assets/f4c0fb35-da4c-40b2-a888-a6673fbe9064" />


open source tools to gets hands on SPICE 
<img width="905" height="247" alt="image" src="https://github.com/user-attachments/assets/b3e8d302-ae5e-4ddc-b102-7d70f7db80f9" />


### L5 Labs Sky130 Id-Vgs 
Simulation for lower nodes. File : Day2 Design file. 

<img width="870" height="224" alt="image" src="https://github.com/user-attachments/assets/b8df4322-8c3c-4d08-b7e7-2b9c0171081e" />

<img width="865" height="797" alt="image" src="https://github.com/user-attachments/assets/e7dca6a4-34ca-42dc-af34-a7a33c6885f1" />

As above, we are doing simulation on for W = 0.39u and L = 0.15u. 
We are doing the Dc simulation, sweeping Vds from 0 to 1.8 v with step of 0.1 

and Vin = Vgs from 0 to 1.8V with step of 0.2


After doing the Spice run of the file 

<img width="1750" height="1023" alt="image" src="https://github.com/user-attachments/assets/151d11b0-b0fd-40c2-89de-a8213b26a4db" />

The lower values of the Vgs it is showing quadratic behaviour and at the higher values of the Vgs it is showing the linear behaviour. The above plot is Id vs Vds for different values of Vgs. We can see for lower values of Vgs it is showing quadratic behaviour and for higher values of Vgs it is showing Linear behaviour. Now if want to see the peak current for Vgs=1.8V, just 'press' left click on mouse at Vgs=1.8V.



<img width="903" height="1037" alt="image" src="https://github.com/user-attachments/assets/7317ba67-d996-44ca-af52-8d9f85d2bedc" />

For Vgs of 1.8v, the peak current is measured as 196uA



**Similary, if we want to see for Id Vs Vgs.**

<img width="900" height="1048" alt="image" src="https://github.com/user-attachments/assets/ab8b5de2-7694-46fd-ab30-e8ae87c27a5b" />


<img width="908" height="947" alt="image" src="https://github.com/user-attachments/assets/d594bbd6-8086-4cc7-9b17-770df572edb8" />

Here we are giving only one specifice Vgs value to observe the characteristics. 
<img width="772" height="997" alt="image" src="https://github.com/user-attachments/assets/4cb4a01c-9578-4aea-b0e7-7eb95e81e075" />
AS we have taken the length as 0.15u -- the short channel, you can observe the linear behaviour. 
Here again we are taking values for L=0.15u and W=0.39u, Keeping Vds constant at 1.8V and sweeping Vgs from 0 to 1.8V with step of 0.1V.</br>

### L6 Labs Sky130 Vt
Now we will calculate Threshold Voltage Vt for Id vs Vgs curve.

<img width="973" height="767" alt="image" src="https://github.com/user-attachments/assets/dc337dde-2aeb-43fd-b21a-0ea758613f77" />

In the curve we can see that Vt is the value when current increases drastically for small change in Vgs. To calculate we will draw tangent on the curve and see where it touches.</br>

<img width="321" height="43" alt="image" src="https://github.com/user-attachments/assets/8caedd5e-d272-4711-a806-aa873bb38b99" />


It comes at around 0.74V.

## CMOS voltage transfer characteristics (VTC)

### L1 MOSFET as a switch

Mosfet as a Switch point of view. 

<img width="871" height="387" alt="image" src="https://github.com/user-attachments/assets/68f668f7-aad3-44df-b5f1-fb25092dda30" />

When |Vgs| > |Vt| ---> Transistor ON ---> Act as closed switch 
When |Vgs| < |Vt| ---> Transistor OFF --> Act as open switch 

![WhatsApp Image 2026-02-24 at 19 21 37](https://github.com/user-attachments/assets/2a99669a-69b8-4a91-b1c9-ca2f61eecfb3)

<img width="901" height="511" alt="image" src="https://github.com/user-attachments/assets/5eaa93e1-9368-4f9a-92df-d27d04b2294a" />

### L2 Introduction to standard MOS voltage current parameters

Equavlent circuit for the CMOS Inverter, as we need circuit for Vin -- High and Vin -- Low. Merge those circutis and try to find out the voltage transfer Characteristics ( VTC ) of the CMOS. That will be used to derive the delay of any cell. 

Now Vin is low and Equal to 0V. 

For PMOS to turn ON -- Negative Vgs  < Negative Vt 
For NMOS to turn ON --- Positive Vgs > Positive Vt


==> for PMOS here, |Vgs| > |Vt| -- Transistor ON
To represent an ON transistor we will symbolize in resistor, as there are physcial elements like wires have resistance ( as the wires got width, depth, length ) 
this resistance is the non linear function of the drain current. 

<img width="892" height="510" alt="image" src="https://github.com/user-attachments/assets/c0b513db-24c0-4794-b44a-678703b5fb99" />

We need to find the currents, which determine the voltage transfer characteristics

When Vout = vdd. ===> Vout = 0. 
Vout to be zero, if your capacitance is completely charged, all the charge present in the capacitor wil discharge through this Rn and as a result of that potential at that point wil be zero. 

Direction of the current is also mentioned. 


Now when Vin = 0, 
In this condition, there is a direct current flow from Vdd to the CL, there by charging the capacitor, as a result Vout = Vdd. 
Direction of the current is also mentioned. 
<img width="883" height="518" alt="image" src="https://github.com/user-attachments/assets/eedfe1e4-29d8-4a58-9c48-dee7aa3fc54a" />

Summary of the above. And also mentioned the Naming convention of the CMOS 

<img width="883" height="514" alt="image" src="https://github.com/user-attachments/assets/9d153408-29e2-422f-8ac8-5a330f1b6e76" />

### L3 PMOS/NMOS drain current vs drain voltage

Voltage transfer characteristics is purely fucntion of the voltage. Everything we go around digital circutis is about voltages. What output voltage we are getting for the provided input. 
It should all need to be function of voltage. 

<img width="881" height="502" alt="image" src="https://github.com/user-attachments/assets/d86ce745-47ce-4306-b422-77931c48a83e" />

<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/66c32ef5-f81f-4459-9db3-c83dfeb37860" />


ALso the current in both the condition is Idsn(drain to source for NMOS) and Idsp(Drain to source for PMOS)
And **Idsp = -Idsn**, both are opposite in direction to each other.
 
Now NMOS IdsN vs VdsN Curve and PMOS IdsP Vs VdsP Curve. 

<img width="1919" height="1055" alt="image" src="https://github.com/user-attachments/assets/148cbcb3-8d54-40d0-a2c6-532ef3ac69a4" />

For NMOS 
VgsN1 --> one of the gate to source voltage for NMOS, it was at zero potential, so the Id = 0 
VgsN2 --> when you increase the Vgs to suffcient value, at point which is just above your threshold voltage  ( NMOS turns ON ) that is the Id curve. Similarly VgsN3 
We increase further more till we achieve the maximum saturation VsgN which is VgsN5 

For PMOS. 
It is due to the direction, we are seeing Negative sign fo the IdsP 
Negative -VdsP is what potential you are giving the NMOS to turn ON, the reverse potential you needed to give to turn ON the PMOS. 

-VdsP ---> which is less than -Vt ---> -Vt Threshold voltage for PMOS--> PMOS OFF--> -IdsP = 0 
-VgsP1 --> as when you start increasing the negative VgsP to more negative side, it becomes more and more lesser than the Vt pf PMOS. Means the PMOS already crossed the threshold voltage level as a result of that there is a Drain current flow. 

-VgsP5 -- at this the maximum drain current is flowing. 

These two curves will be helpful in deriving the voltage transfer charactertistics of the CMOS inverter. 

### L4 Step1- Convert PMOS gate-source-voltage to Vin

PMOS is just an inversion of NMOS. Internal node voltages will not be visible in terms of the logic circuits, there will be only Vin and Vout, we need to find the function in terms these. 

Whenever the Vin sweeps from input logic  0 to 1 the Vout goes from logic 1 to 0. The time in which it goes Logic 1 to 0 (Vout)  on the application of the Vin ( 0 to 1 ) is the *'Delay'* of the cell

We need to convert these curves as function of Vin and Vout. 

<img width="902" height="509" alt="image" src="https://github.com/user-attachments/assets/416e9b8b-db54-4106-aaf6-a9f9f2388e60" />

[Below are the steps to Obtain voltage-Transfer Characteristics (VTC) for Static CMOS Inverter.] 
These steps are applicable for the CMOS inverter of any Node. 
**Step 1**
1. We shall take all the possible values of the Vgsp ( 5 different Values)
   <img width="304" height="215" alt="image" src="https://github.com/user-attachments/assets/8d87a2ef-4668-4159-b833-b12a7a3d624e" />

2. Assume it is a long Channel Device. Also Assume Vdd = 2V
   
3. As we know that VgsP = Vin - Vdd ==> finding the Vin using this equation.
<img width="890" height="234" alt="image" src="https://github.com/user-attachments/assets/f569b7b9-3289-4eeb-853c-d15c77257d63" />

4. By Observation IdsP = -IdsN, we are shifting the curve i.e we  are plotting the Vin value for evey VgsP. By this shift we have got rid of the VgsP. 

<img width="600" height="519" alt="image" src="https://github.com/user-attachments/assets/20fffa70-9ea3-472e-9535-a42c633bf317" />

We will try to plot the graph of PMOS in terms of IdsN, the plot will be as shown above. We can see that the corresponding Vin value of VgsP is being plotted as shown in the above table.


### L5 Step2 & Step3- Convert PMOS and NMOS drain-source-voltage to Vout

**Step 2:** -- Convert the VdsP as the function of the Vout. 
1. We know that VdsP = Vout - Vdd ==> Vout = Vdd + VdsP 

<img width="937" height="528" alt="image" src="https://github.com/user-attachments/assets/764ce8de-a725-437e-94c0-4cc091c98f9a" />

 Looking by the Equation Vout = Vdd + VdsP, if your VdsP = -2v  for the Vdd = 2V, Your Vout=0V
 Similarly for the VdsP -2V, Vdd = 2V, Vout = 0V, Vin ( gate voltage ) = 1.5V  there is a finite current flowing, as Output capacitance is discharged, we need to charge the capacitor. 
 
We can see that whenever Vout=2V that means Vdsp=0V and Vdd=2V (given), then The current is zero and capacitor at the output is discharged. This is true only when PMOS is in combination with NMOS and forms a CMOS inverter
These curves are only obtained whenver there is a CMOS logic involved.( PMOS + NMOS ) 

At every gate voltage of Vin, we can see there is finite amount of current present at Vout=0V. 
Reason is whenever the Vout = 0, capacitor at output is completely discharged, you need to charge it, so we need some Charging current to get charge. So, here we get the load curve for PMOS.  

As everything is the function of the Vin and Vout, these curves are now called as Load Curve for PMOS transitor. ( there is no dependency on VgsP, IdsP, VdsP ) 



**Step 3:**Now, we will try to get the Load curve for the NMOS transistor. 

<img width="901" height="521" alt="image" src="https://github.com/user-attachments/assets/7437c40d-61ff-4814-b498-eccbeeb327f9" />

It is actually simple as VgsN = Vin and VdsN = Vout, directly we can get the graphs


Voltage Transfer characteristics of the CMOS can be obtained by merging the Load Curve for NMOS and PMOS transitor. 

<img width="907" height="340" alt="image" src="https://github.com/user-attachments/assets/fb31ac89-16a0-4cec-8b5c-f95e68c3f91b" />


### L6 Step4- Merge PMOS-NMOS load curves and plot VTC
Voltage Transfer characteristics of the CMOS can be obtained by merging the Load Curve for NMOS and PMOS transitor. 

We will superimpose the Load curver of NMOS on the Load Curve of PMOS. The reason we are doing this is , as we have Vin and Vout which is common for the whole CMOS,  if we want to derive the VTC it has to be the intersection points between between the NMOS and PMOS load curves 


<img width="934" height="302" alt="image" src="https://github.com/user-attachments/assets/e4d66b09-2912-49b8-befb-ad02ef047217" />

Vin axis from 0 to 2V and the Vout axis from 0 to 2V. 

We will plot the Vin vs Vout from the above graph, from the intersection points of the PMOS and NMOS load curves. 

* When Vin = 0, then Vout = 2 , at this Point -- NMOS = OFF (Cut off); PMOS = ON ( linear)
* When Vin = 0.5V, 1.5 < Vout < 2, -- NMOS ( Saturation) ; PMOS ( linear )
* When Vin = 1V, 0.5 < Vout < 1.5 -- NMOS ( Saturation) ; PMOS ( Saturation)
* When Vin = 1.5V, 0 < Vout < 0.5 -- NMOS ( Linear ) ; PMOS ( Saturation)
* When Vin = 2V, Vout = 0V --- NMOS (Linear) ; PMOS (Cut-Off) 

<img width="889" height="520" alt="image" src="https://github.com/user-attachments/assets/e6b62049-fb37-4b35-b9e3-15739b98b434" />
VTC of the CMOS logic. 

This VTC ( by this techinque ) will help us understand the Digital and analog parts of the circuit. Also make us understand at what state te PMOS and NMOS are whenever you switch /transit from 0 to 2.  

More explanation in the below images. 

<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/abe185a1-7e80-4a5f-95c3-6201919659f9" />

<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/6b28f645-2318-458b-9411-be7796d4ead6" />


<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/50a8ea55-3c30-4d9c-8c79-444ef629d386" />

<img width="629" height="280" alt="image" src="https://github.com/user-attachments/assets/2d681cfe-489e-4296-b69d-02e78e135051" />


# NgspiceSky130-Day3-CMOS switching threshold and dynamic simulations

## Voltage transfer characteristics-SPICE simulations

### L1 SPICE deck creation for CMOS inverter

we will do the simulation for the VTC. For that we need to **create the SPICE deck**. It has the connectivity information, (inputs which neeed to provide) about the netlist. We need to create SPICE deck for the whole netlist. 
 IN SPICE DECK 

* Component Connectivity

PMOS ---> Arrow pointing outside ( representing Substrate )  
NMOS --> Arrow pointing inwards ( representing Substrate )

The value of the output load capacitor comes after a lot of theories, and it should be determined by considering a characteristics and calculations, for now we are assuming as 10fF. 

* Component values are assigned. 
Note: Ideally PMOS should be 2 or 3 times bigger than NMOS. But for now we are taking the same width for both NMOS, PMOS.

* Next defining the values of the input gate voltage and output voltage. 
<img width="889" height="434" alt="image" src="https://github.com/user-attachments/assets/98708e55-ab24-46cc-a613-1251c88b1d9d" />


* Next we have identify the nodes. ( as node is two points which has a component between them)
  Nodes are basically required to define the SPICE NETLIST
  <img width="519" height="425" alt="image" src="https://github.com/user-attachments/assets/cb72d395-2b26-438f-aec5-de99480375b0" />

* **Name the nodes** In model file we will mention like, 2.5V input lies between Vin and 0, similarly Vdd lies between vdd and 0.

  <img width="364" height="343" alt="image" src="https://github.com/user-attachments/assets/4929047e-5fda-44aa-a9a4-80dd41fccb0d" />

Lets start writing the SPICE DECK: 

<img width="887" height="442" alt="image" src="https://github.com/user-attachments/assets/38d3db3a-382e-465e-a25e-7e32e53f8ba7" />

Syntax : DGSS ( Drain Gate Source Substrate )  or DGSB ( Drain Gate Source Bulk ) 
M1 is the name of the transistor of type pmos. 

### L2 SPICE simulation for CMOS inverter

M2 is for the NMOS transistor 

<img width="874" height="458" alt="image" src="https://github.com/user-attachments/assets/75e060b1-d3b9-4b37-84a3-229cd365f889" />

<img width="891" height="504" alt="image" src="https://github.com/user-attachments/assets/9826fc28-de11-4ddf-b437-e11c7c6aab44" />
<img width="900" height="480" alt="image" src="https://github.com/user-attachments/assets/943bde5e-f4b8-4d9e-bf2c-5950ccc87552" />
<img width="887" height="432" alt="image" src="https://github.com/user-attachments/assets/68013985-0e89-4f63-8e67-3b882b0379a0" />

Simulation commands
<img width="889" height="500" alt="image" src="https://github.com/user-attachments/assets/888e3b22-5e8b-481a-b81e-e220dcfc7d62" />
we will be sweeping the input voltage from 0 to 2.5V with the step of 0.05V and measuring the Vout or output waveform

Describing the model files -- This the file from which takes the description of the NMOS and PMOS is taken.  In this file you will see an attributre for PMOS and NMOS and all the description and parametets of nmos and pmos are present respectively. 
<img width="876" height="442" alt="image" src="https://github.com/user-attachments/assets/32b5a2a7-5074-4260-81e3-87485a330e20" />


SPICE Simulation for the Wn = Wp = 0.375u ( Channel Width ) ; Ln = Lp = 0.25u ( Channel length) for the device 
and Wn/Ln = Wp/Lp = 1.5 

model file : 
<img width="636" height="480" alt="image" src="https://github.com/user-attachments/assets/cd9a2ef8-5957-45b4-818a-c717477a6ebc" />
<img width="634" height="470" alt="image" src="https://github.com/user-attachments/assets/247cf565-c670-47cb-8e9e-faa04ce4dc7f" />

Netlist
<img width="636" height="464" alt="image" src="https://github.com/user-attachments/assets/e7d901eb-fcb7-49bc-83bc-07b1abb75b8d" />

<img width="609" height="356" alt="image" src="https://github.com/user-attachments/assets/3c0f804a-55a7-46fd-a6c5-6250b1a7b7a6" />

Waveform of VTC : 
<img width="683" height="483" alt="image" src="https://github.com/user-attachments/assets/89e8e764-315d-4f1a-97b3-3b7b10bfab50" />


NOW, 

SPICE Simulation for the Wn =0.375u ,  Wp = 0.9375u ( Channel Width ) ; Ln = Lp = 0.25u ( Channel length) for the device 
and Wn/Ln =1.5 , Wp/Lp = 2.5 

The width of the PMOS transitor is 2.5 times more than the NMOS transistor 

Spice deck for the changed PMOS width values : 
<img width="640" height="473" alt="image" src="https://github.com/user-attachments/assets/b002e105-91c5-44f7-9e25-21efee23697b" />

And executing: 
dc2
<img width="548" height="448" alt="image" src="https://github.com/user-attachments/assets/cc2a927a-1cb6-430a-a8d7-accd46a97f00" />

If we observe the previous graph is left shifted slightly. This happens because NMOS is more stronger than PMOS in previous graph.


### L3 Labs Sky130 SPICE simulation for CMOS

<img width="885" height="243" alt="image" src="https://github.com/user-attachments/assets/151cab39-e2f7-4a1a-885e-465da4c80aa3" />
<img width="893" height="795" alt="image" src="https://github.com/user-attachments/assets/49662a5a-134e-4c61-81a7-779de1bce32f" />

We are using both pfet and nfet for CMOS inverter. We can see that W/L ratio of pmos is 2.33 times greater than that of nmos.

To get the plot type `ngspice` and `plot out vs in`.

<img width="826" height="795" alt="image" src="https://github.com/user-attachments/assets/2598a842-9cc6-440f-85a8-fc88cb4d0e8b" />

This is the VTC Characteristics of the CMOS inverter

<img width="845" height="805" alt="image" src="https://github.com/user-attachments/assets/6e53b0b2-a3fc-4b40-8f03-364c2fe4cfc6" />

We need to find the switching Threshold - It is the point where Vin = Vout. 
For zoom in, select the area. 
 press righ mouse button + hold it.


<img width="1865" height="1118" alt="image" src="https://github.com/user-attachments/assets/3b324992-91a6-4abd-9d22-5b666abeeb3f" />


<img width="267" height="38" alt="image" src="https://github.com/user-attachments/assets/c8a9f0d0-0b5a-4cdf-9a99-7e4affc90c27" />

So switching threshold for W/L=2.3 is around 0.876V

Transient Analysis: 
<img width="1498" height="216" alt="image" src="https://github.com/user-attachments/assets/6f0d6d4d-73dd-4663-842f-8ea705af4744" />

in transient analysis, we are giving the pulse signal ( 0 to 1.8v with shift of 0, rise time and fall time of 0.1 ns., with pulse width of 2ns, total time period of 4ns ) 

<img width="572" height="644" alt="image" src="https://github.com/user-attachments/assets/3e085cb8-a441-4ac8-8002-05bf533c2982" />

<img width="1781" height="132" alt="image" src="https://github.com/user-attachments/assets/9afc7f43-4aeb-44bc-a0b7-a969b19cf15b" />

<img width="1728" height="885" alt="image" src="https://github.com/user-attachments/assets/1f768635-e5e5-4650-8a2b-2d72e8654d4e" />



We need to calculate Rise delay and Fall delay, we have to consider 50% of Vdd. I.e (1.8 / 2 )=0.9 . So for rise delay and fall delay, we need to consider 50% of output curve i.e. at 0.9V; 
<img width="731" height="552" alt="image" src="https://github.com/user-attachments/assets/b1d9584d-3e3a-4d49-9a0a-f54241d0eac4" />

Rise Delay: 
<img width="1742" height="776" alt="image" src="https://github.com/user-attachments/assets/ad7d7f6d-3162-42ac-83b4-4e7f811c1421" />

<img width="612" height="430" alt="image" src="https://github.com/user-attachments/assets/7ffaec6e-ca0a-406d-aa14-0d1039365ebd" />

Output is X out = 2.482 
Input is Xin = 2.15 
Rise delay = 2.482 - 2.150 = 0.332 


Now for Fall Delay: 

<img width="324" height="70" alt="image" src="https://github.com/user-attachments/assets/c1b3d1fa-e95d-4758-98c8-d9c2756978ac" />

Output is X out = 4.335
Input is Xin = 4.050

Fall delay = 4.335 - 4.050 = 0.285 

This is how we calculate the rise delay and fall delay in the Transcient Analysis. 


## Static behaviour evaluation-CMOS inverter robustness-Switching Threshold

### L1 Switching Threshold, Vm
Let us compare the two different CMOS Inverters with Different W/L ratios of PMOS and NMOS, we can basically say PMOS is bigger than NMOS. 
*  Irrespective of the voltage level which they are shifting, the shape of waveform remains the same. -- We can infer that CMOS device is a robust device.
*  When every your Vin is high , output is low and vice versa. This characteristics is maintained for all kinds and sizes of CMOS inverter. That is the reason it is widely used in the circuits / logic gate designing. 
<img width="900" height="447" alt="image" src="https://github.com/user-attachments/assets/58180641-fb27-454e-87da-0f12f58289dc" />

**Static Behaviour Evaluation: CMOS Inverter Robustness**

1. Switching Threshold, Vm :
    * It is the point where Vin = Vout. we will draw a tan 45 degress line and identify the point Vm at which the Vin = Vout.

 For  Wn/Ln = Wp/Lp = 1.5   
<img width="787" height="493" alt="image" src="https://github.com/user-attachments/assets/00aa5c47-8a3e-443d-8d05-918f7249b706" />

For the bigger device 
<img width="739" height="534" alt="image" src="https://github.com/user-attachments/assets/9e95b621-5945-49f4-a8e4-90b7a7bae61b" />

   * In this area, in this point PMOS and NMOS both are in saturation. The both are kind of turned ON, if both are turned On there is a chance of Leakage to the ground.
   * Switching Threshold values
     <img width="850" height="495" alt="image" src="https://github.com/user-attachments/assets/6cf551c4-453a-4a18-bb78-cc63c0964a89" />
   * Both Turned ON -- beacuse the gate voltages are very much above Vt.
   * Curent flows from both the transistors ( direction mentioned in the below image ) 

<img width="907" height="506" alt="image" src="https://github.com/user-attachments/assets/47773b0d-115a-48a1-b589-9ae5bd2280b6" />


### L2 Analytical expression of Vm as a function of (W/L)n and (W/L)p

* We will now calculate the value of Vm w.r.t the NMOS and PMOS width and length.

<img width="895" height="497" alt="image" src="https://github.com/user-attachments/assets/1509378e-dc18-4975-902d-22ecfb3eb2c0" />

we will ignore the ( 1 + lamda * Vds ) as Lamda is very close it zero and when you calculate that whole term will come close to 1. 

<img width="897" height="502" alt="image" src="https://github.com/user-attachments/assets/fe338604-d1d2-42ef-bbba-ae83842fcb62" />

<img width="886" height="503" alt="image" src="https://github.com/user-attachments/assets/478a106c-a69e-4a3f-833f-a3aa26ea905f" />

We will get the values of the Kp'and Kn' (process transconductance)  and Vdsatn and Vdsatp from the model files 
Subsitute the values in the above mentioned equation to get R. and R substitute you will get Vm. 
When you solve the equation for value of Vm, we get it as 0.98v


### L3 Analytical expression of (W/L)n and (W/L)p as a function of Vm
Now here we will calculate the value of W/L for PMOS and NMOS when Vm is given.
We have to move in reverse fashion, as we need to calculate W/L ratio of PMOS and NMOS such that Switching threshold is exatly half of the power supply Vdd = 2.5V, therefore required Vm = 1.25V.
We will set the Value of Vm here, Alternatively the required ratio of PMOS vs NMOS transistor size can be derived such that Vm is set. 

We will start from the current equation itself i.e. **Idsn = -Idsp**

Expanding Kp and Kn (Gain factor) </br>


<img width="874" height="406" alt="image" src="https://github.com/user-attachments/assets/ce78a54b-d439-4d59-811b-b6d6503e2585" />

<img width="831" height="458" alt="image" src="https://github.com/user-attachments/assets/f5aaf49e-5875-4093-be97-6eae9ee843de" />

<img width="861" height="466" alt="image" src="https://github.com/user-attachments/assets/bfc4c43a-a7ac-455d-8885-bb2b04d89f96" />

<img width="421" height="115" alt="image" src="https://github.com/user-attachments/assets/8494f23c-c235-4101-8bf6-0da619dd27b5" />

<img width="383" height="102" alt="image" src="https://github.com/user-attachments/assets/9da2d153-ac81-4e5f-b593-458ab972148b" />

You keep the set value of the Vm and rest of the constants which we get in the model files, You can get the W/L ratio, like PMOS is N times the NMOS. based on that you can decide the values. 

<img width="828" height="500" alt="image" src="https://github.com/user-attachments/assets/d65ed102-df3a-4e8a-8cb6-e83ca979d232" />

### L4 Static and Dynamic simulation of CMOS inverter

**For (W/L)n = (W/L)p = 1.5**
<img width="533" height="438" alt="image" src="https://github.com/user-attachments/assets/023a7139-0874-48ad-bd43-39aa0ce4838e" />


<img width="843" height="372" alt="image" src="https://github.com/user-attachments/assets/6cd0991a-2eb7-4534-ad74-fdf91074a34d" />

We are going to feed the above pulse as an input and perform the transient analysis
We can also calculate the "Rise Delay" and "Fall Delay" by using the transient analysis
<img width="885" height="499" alt="image" src="https://github.com/user-attachments/assets/22b81f48-e6c9-4877-a27a-5db4f56d353c" />

### L5 Static and Dynamic simulation of CMOS inverter with increased PMOS width
We will be doing the SPICE simulations for increased width of PMOS transistors and compare the results.

**For (W/L)p = (2W/L)n, width of pmos is double the size of nmos **
<img width="346" height="237" alt="image" src="https://github.com/user-attachments/assets/c9c3168f-7105-48d0-903d-99e9b7ac0fbe" />

If we compare with the previous one, the DC characteristics have been shifted to the right side. 
<img width="542" height="434" alt="image" src="https://github.com/user-attachments/assets/84e446fb-eb66-4ab8-bb7e-76308cb6515d" />
As the PMOS has become stronger than NMOS, you have more area in the PMOS load capacitor to charged, it gets charged very fast. 

<img width="898" height="509" alt="image" src="https://github.com/user-attachments/assets/8bedbe2f-b648-4d7a-9776-7bb6d9c14c2a" />

From the last case, the Vm has moved from 0.99 to 1.2V, the reason is size of PMOS has been increased. Area available for the PMOS to charge the load capacitor has been increased. As a result of that whenever the input switches from logic 1 to logic 0 , there is more amount of room available for the PMOS to charge and discharge. 

**For (W/L)p = (3W/L)n, width of pmos is thrice the size of nmos
<img width="884" height="505" alt="image" src="https://github.com/user-attachments/assets/d6cba8db-1d9e-4f19-8ab7-ea20917b1fe8" />

further increasing the width of PMOS 
<img width="894" height="503" alt="image" src="https://github.com/user-attachments/assets/ffd08204-23fc-42f0-b9c4-51b2ff517a5b" />

<img width="882" height="497" alt="image" src="https://github.com/user-attachments/assets/3ec9730c-cbfd-4b64-a9bc-d1c0ba0531e1" />

Rise Delay -- It says that the time required by the output capacitor to charge completely. And the Rise delay has been significantly got reduced as the width is increased. Reason is we have bigger area 

<img width="893" height="502" alt="image" src="https://github.com/user-attachments/assets/65277ddf-c044-4b31-8d60-d9a4648223db" />

### L6 Applications of CMOS inverter in clock network and STA

Observations from the above experiment : 
* If you vary the PMOS size, lets say from 2times or 3 times the width of the NMOS, we can observe there is no much diffference in the Vm voltage. Hardly a 50 mV difference. With this we can say that During Fabrication, there can be slight variation in sizes of PMOS and NMOS from the expected one. But the robutness of CMOS inverter is such that, there is not much difference in the Vm with change in sizes.


* When (W/L)p = (2W/L)n, in this case we can see that the rise delay and the fall delay is approximately equal, if we design the CMOS with Switching threshold Vm = 1.22.. or 1.23 we can obtain the eqaul rise and fall delay  and form a Symmetry cell.

*This is a typical characteristic of Clock Inverter/buffer where we want the rise delay and fall delay to be equal.*
<img width="891" height="494" alt="image" src="https://github.com/user-attachments/assets/47f857aa-9d85-44e0-8769-6bc423a0c1e5" />

<img width="876" height="498" alt="image" src="https://github.com/user-attachments/assets/ba9f1278-f678-4f68-b558-3aa4f4b64937" />


<img width="887" height="456" alt="image" src="https://github.com/user-attachments/assets/ee83a974-17c9-4861-8e05-90cba426f695" />
Other types of cells can be used according to the data path requirement


<img width="897" height="503" alt="image" src="https://github.com/user-attachments/assets/c34a52a3-96d0-4781-9a0d-590979e470b1" />

Revisit this last video again. 




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


































































  

























































  
