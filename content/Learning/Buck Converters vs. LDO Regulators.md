So I was prepping for the design of a simple microcontroller development board, and realized that I would need to get 3.3V from 5V. Obviously, this requires some form of voltage step down.

Upon research, I discovered three main methods of stepping down voltage.

1. Voltage divider
2. Buck converter
3. LDO regulator

Each of these methods have their own pros and cons based on how they work. In this section I want to document the learning that I did to understand when to use each of these three methods of stepping down voltage and the working principles of the components.

### Voltage Divider

The voltage divider is the easiest way to step down a voltage but comes with many drawbacks that are often dealbreakers. For one, it only works with a constant resistive load, because the load in parallel with the bottom resistor of the voltage divider causes the output voltage to dip. This means you would need a buffer circuit with an operational amplifier or readjust the resistor values to ensure you're getting the output voltage you need. 

Another drawback is current; since the current is being sent through two resistors, a lot of energy is dissipated as heat. Additionally, the current is being split at the load and the bottom resistor, which might not even be enough for your application. Increasing the resistor values to increase efficiency and reduce waste current just makes the output voltage easy to upset with a load in parallel (as mentioned above), while decreasing the resistor values to drive loads with less error generates way more heat.

In short, a voltage divider is useful for getting a reference voltage, but is probably not your best choice for driving any sort of load. 


### Buck Converter

The buck converter is also known as a specific type of DC-DC regulator where the output voltage is less than the input voltage. The buck converter achieves the voltage drop with a switching component; by switching on and off, the average voltage across the load for a certain time period will decrease. This on and off switching action creates an AC square wave, and a low pass filter is then used to smooth out the wave and effectively convert it back to DC. The diode, also known as a freewheeling diode, is in place to ensure that current does not flow backwards into the switching component. 

It can be shown that the equation that relates the input voltage, output voltage, and duty cycle of the buck converter is:

$$Vout=Vin*D$$

where $D$ is the duty cycle, or the ratio of the time when the switch is on to the period of the on-off cycle of the switch. The lower the duty cycle, the lower $Vout$ will be.

The buck converter is an excellent option for efficiency as little heat is dissipated in the circuit and handles higher currents. However, the due to the nature of switching regulators, there tends to be a good amount of noise generated due to the ripple from the low pass filter. The buck converter is great for stepping down large voltages without many losses, and when you can tolerate a little bit of noise.

### LDO Regulator

LDO stands for linear drop-out, meaning that there is a specific dropout voltage value (which differs between specific components) that guarantees a regulated output voltage. The inequality that describes an LDO regulator is:

$$Vin>Vout+Vdropout$$

The LDO regulator takes advantage of pass elements (MOSFETs or BJT) in their ohmic region. This is the region of transistor operation where the element acts close to a resistor, hence the name ohmic. The region that you are operating a transistor in depends on the gate-source voltage $Vgs$, drain-source voltage $Vds$, and drain current $Ids$.

![[Pasted image 20250527180659.png]]

>The image above is from an [Infineon application note](https://www.infineon.com/dgdl/Infineon+-+Application+Note+-+PowerMOSFETs+-+OptiMOS%E2%84%A2+-+Linear+Mode+Operation+and+SOA+Power+MOSFETs.pdf?fileId=db3a30433e30e4bf013e3646e9381200), and describes the output characteristics of a power MOSFET. 

as a variable resistor; when combined with the error amplifier, changes in $Vin$ result in a constant $Vout$. This method of operating the pass element in the ohmic region allows for a very small dropout voltage, all while doing active regulation, which is something a simple voltage divider cannot do.

It's really easy to get into the nitty gritty of LDOs and how their performance varies at different temperatures, output currents, and voltage differentials. For example, the maximum output current massively decreases as you increase the voltage differential, and the dropout voltage value increases as output current increases. This means that selecting the correct LDO component is crucial to making sure that you get the outputs that you want. All of this information should be checked against the datasheet of the specific LDO that you want to use.
