# CR-10S

This guide will go through the process of hooking up your QuadFusion to Creality's CR-10S printer.

{% hint style="warning" %}
There is no affiliation between M3D/The QuadFusion and Creality 3D/The CR-10.
{% endhint %}

## Mechanically

![](../.gitbook/assets/image%20%2836%29.png)

**You will need...  
-** 3.0mm Standoff \(25mm long\) \(x2\)  
**-** 2.0mm Hex Screws \(x2\)

**Tools  
-** Pliers  
**-** 3.0mm Hex Screwdriver  
**-** 2.0mm Hex Screwdriver

Once you have removed the extruder that comes with the CR-10S, you will want to take of the mounting plate and drill holes using these specs:

![](../.gitbook/assets/image%20%2862%29.png)

Place the newly drilled plate back on to your CR-10S, attach the top two wheels if you removed them.

![](../.gitbook/assets/image%20%2846%29.png)

Next, thread the two 2.0mm Hex Screws through the holes you have just drilled.

Once you have done this, you will want to attach the two 25mm long standoffs to the QuadFusion head.

![](../.gitbook/assets/image%20%2811%29.png)

You can now, by threading the 2.0mm Hex Screws into the standoffs, mount the QuadFusion head onto the CR-10S.

Lastly, attach the bottom wheel:

![](../.gitbook/assets/image%20%2834%29.png)

You have now fully attached the QuadFusion to your CR-10S.

## Electrically

{% hint style="info" %}
You will need a Duet Maestro board if you wish to follow along during the electrical part of this guide. Look at the bottom of the page to see where to get one.
{% endhint %}

{% hint style="info" %}
Go to this link: https://www.thingiverse.com/search?q=Duet&dwh=345c37c6245e907   if you want to print a Duet Holder. These can be very helpful with protecting and organizing your Duet Maestro!
{% endhint %}

**You will need...  
-** 24V Power Supply  
**-** Duet Maestro Board  
**-** Duet Maestro Expansion Board  
**-** Jumper

**Tools  
-** Flat-Head Screwdriver

This is the Duet Maestro:

![https://duet3d.dozuki.com/Wiki/Duet\_2\_Maestro\_Hardware\_Overview](../.gitbook/assets/image%20%2864%29.png)

This will be a walk through on how to connect the QuadFusion & CR-10 to your Duet Maestro Board with the Extruder Expansion board.

Before you can begin to wire your QuadFusion to the Duet Maestro board you must attach an extension to the board. With this extension you will be able to connect the the extra motor wires to the board.

The following pictures show where the extension goes, and how it looks once it has been plugged in:

![](../.gitbook/assets/image%20%2889%29.png)

![](../.gitbook/assets/image%20%282%29.png)

Additionally, you will need to attach a jumper to the pins next to the expansion board:

![](../.gitbook/assets/image%20%2812%29.png)

#### Base Connections

![](../.gitbook/assets/image%20%288%29.png)

Without the fans, the QuadFusion has six main wires coming from it. The four wires with yellow dots at the ends are the motor wires. The wire with a green dot is the heater wire, and lastly the wire with the red dot is the thermistor.

The wires plug in to their corresponding color that is boxed in the following picture:

![](../.gitbook/assets/image%20%2870%29.png)

Notes:

* Keep in mind when you're wiring your QuadFusion's motors to the Duet Maestro board which motor is connected to which port. The first picture in this guide labels each port as E0 Stepper, E1 Stepper, E2 External Driver, and E3 External Driver. When facing the front of your QuadFusion, the front left motor is 0, the front right motor is 2, the back left motor is 1, and the back right motor is 3. 
* If you decide to extend the wires given to you, make sure that you are maintaining the original positive and negative wires. 

The next steps will be to connect your CR-10S' stepper motors, power source, limit switches, and Z-probe

{% hint style="warning" %}
The CR-10S we worked with used a Z-probe instead of the Z-limit switch the printer came with. Additionally, we ended up having the bed heated separately, which will be explained within the guide.
{% endhint %}

Starting with the stepper motors, there are four motors you should be hooking up. One for the X-Stepper motor, one for the Y-Stepper motor, and two for the Z-Stepper motors.

![](../.gitbook/assets/image%20%2892%29.png)

If you look above, the boxed sections are where you will be plugging in your stepper motors. The color coordination is as follows;  
Yellow = X-Stepper Motor  
Orange = Y-Stepper Motor  
Green = Z-Stepper Motors

Once you have plugged these in you can move on to connecting the power supply. **You will need a 24V power supply** to power your Duet Maestro board

![](../.gitbook/assets/image-32.png)

The three circled wires are what will be connecting your power supply to an outlet. The non circled wires are what will be connected to your Duet Maestro board

{% hint style="info" %}
We recommend having an on/off switch between the power supply and Duet Maestro board, this makes it easier to turn your printer on and off.
{% endhint %}

![](../.gitbook/assets/image-81.png)

The red and black wires will be connected to ports 3 and 4, respectively, as shown in the image above.

Lastly, you'll need to connect the Z-probe and limit switches. Starting with the limit switches:

![](../.gitbook/assets/image-41.png)

The picture above shows where each limit switch should be connected. Color coordination is as follows;  
Yellow = X-Limit Switch  
Red = Y-Limit Switch  
Aqua = Z-Limit Switch

Now, if you are using a Z-probe as we did, you will be connecting the probe to the Duet Maestro board based off of your probe's specific wiring

Go here to understand how Duet wires Z-probes to their boards:  
Choosing a Z-probe: [https://duet3d.dozuki.com/Wiki/Choosing\_a\_Z\_probe](https://duet3d.dozuki.com/Wiki/Choosing_a_Z_probe)  
Connecting a Z-probe: [https://duet3d.dozuki.com/Wiki/Connecting\_a\_Z\_probe](https://duet3d.dozuki.com/Wiki/Connecting_a_Z_probe)

**Attaching the LCD Screen**

To attach the LCD screen to your Duet Maestro you will need to use these ribbon cables provided in the upgrade kit given to you. You will plug the cables into the Duet Maestro in ports labeled "Future Expandability" 

![](../.gitbook/assets/image%20%2864%29.png)

Finally, attach the cables to your LCD screen.

**Heating the Bed**

The bed was wired separately from the main collection of wires because of the power supply. The QuadFusion requires a 24V power supply in order to properly power the motors, heater, and thermistor. However, the bed could only be safely powered by 12V, so it was decided to have the bed remain wired to Creality's original board. Because of this, you will be able to heat your bed from the control block that comes with the printer, as opposed to heating with the Duet Web Control.

Don't have something that is listed here? Check out these links if you need something for the QuadFusion!

24V power supply: [https://store.printm3d.com/collections/parts/products/400w-power-supply?variant=12283391148110](https://store.printm3d.com/collections/parts/products/400w-power-supply?variant=12283391148110)  
Duet Maestro Board: [https://fitforlaunch.com/projects/duet-2-maestro](https://fitforlaunch.com/projects/duet-2-maestro)  
Extruder Expansion Board: https://store.printm3d.com/products/copy-of-duet-2-maestro-expansion?variant=21198635434062                   
Toggle Switch: [https://store.printm3d.com/collections/parts/products/lighted-toggle-switch?variant=12283706245198](https://store.printm3d.com/collections/parts/products/lighted-toggle-switch?variant=12283706245198)


Thank you for supporting the QuadFusion, and Happy Printing!

