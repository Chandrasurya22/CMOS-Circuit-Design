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

