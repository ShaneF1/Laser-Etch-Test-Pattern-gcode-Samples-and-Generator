I built a more or less DIY CNC laser. In learning how to properly use it I realised I needed some test patterns to help me understand and optimise the speed and power requirements of the laser for different types of material and colours.

All I needed was "just the gcode". I didn't want to install a web server, or python or spend $150 of a piece of software that I would only use a handful of times. I couldn't find either "just the gcode" or a simple way of doing this.

So I did what any frustrated engineer would do. I overcompensated.

In searching for gcode constructors I found "gcmc - G-Code Meta Compiler" by Vagrearg at https://www.vagrearg.org/content/gcmc. This stroke of genius compiler is a simple download having no installation requirements. So here is the code I wrote to produce the test patterns and the more useful actual "just the  gcode" samples I have been using regularly. If you need test patterns with different behaviours the gcmc code is hopefully documented enough that you can easily create your own gcode.

The gcode samples provided produce an 8x8 grid of 5mm squares at 0.1mm line spacing with varying speed and power levels and fit inside a 90mm square test pattern. All the samples provided scale the speed "x" axis from 100mm/min to 1000mm/min. The various code samples scale the power "Y" axis from 10 to 125, 50 to 250, 125 to 500 and 250 to 1000 as described in their titles. The 1000 power value equates to 100% laser power in my machine.

Note that if creating your own gcode, the power levels can be described as positive values which map to a M3 gcode command or negative values which map to an M4 gcode command. I find the M4 gcode command more useful and indicative as M4 will have your grbl controller dynamically scale laser power in response to the dynamics of your machine movement. The gcode samples provided use negative power values and M4 commands.

# Examples:

Below are examples of test tiles etched using these patterns:

![20221014_190427 small](https://user-images.githubusercontent.com/7357540/195807971-7a5dc79e-d842-43bb-8d62-ee8ab9bdc0c2.jpg)
![20221014_190454 small](https://user-images.githubusercontent.com/7357540/195808443-a05204f7-d627-4eea-9ae5-0c49cd9e52c6.jpg)

and a sample of what can be done with the right speed/power levels:

![20221014_190515 small](https://user-images.githubusercontent.com/7357540/195808003-41a7fec6-881b-4220-8b38-f8856e8b330f.jpg)

# References:

"gcmc - G-Code Meta Compiler" by Vagrearg at https://www.vagrearg.org/content/gcmc
