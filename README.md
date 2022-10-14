## Need

I built a more or less DIY CNC laser. In learning how to properly use it I realised I needed some test patterns to help me understand and optimise the speed and power requirements of the laser for different types of material and colours.

All I needed was "just the g-code". I didn't want to install a web server, or python, or javascript, or spend $200 on a piece of software that I would only use a handful of times and cost more than my build. I couldn't find either "just the gcode" or a simple way of doing this.

So I did what any frustrated engineer would do. I overcompensated.

## Solution

In searching for g-code constructors I found "gcmc - G-Code Meta Compiler" by Vagrearg at https://www.vagrearg.org/content/gcmc. This stroke of genius compiler is a simple download having no installation requirements. So here is the g-code generator I wrote to create the test patterns and the more useful actual "just the  g-code" samples I have been using regularly. If you need test patterns with different behaviours the g-code generator is hopefully documented well enough that you can easily create your own g-code.

## g-code Samples

The g-code samples provided produce in my case an 8x8 grid pattern of 5mm squares at 0.1mm line spacing with varying speed and power levels and fit inside a 90mm square. All the samples provided scale the speed "x" axis from 100mm/min to 1000mm/min. The various samples scale the power "Y" axis from 10 to 125, 50 to 250, 125 to 500 and 250 to 1000 as described in their titles. The 1000 power value equates to 100% laser power in my machine.

Note that units are NOT set in the g-code so whatever your machine is set to will apply. You MUST verify the g-code is appropriate for your configuration.

## g-code Generator

The g-code generator constructs the g-code test pattern starting at the highest speed and progressively higher power. In practice I wanted to use the highest speed and lowest power level to achieve a result. These speed/power patterns are etched first (right to left) so the etch can be truncated if the needed results are provided early. The g-code generator provides for adjustment of row/col count, min/max speed, min/max power, box size and line spacing.

Note that if creating your own g-code, the power levels can be described as positive values which map to a M3 g-code command, or negative values which map to an M4 g-code command. I find the M4 g-code command more useful and indicative as M4 will have your grbl controller dynamically scale laser power in response to the dynamics of your machine movement. This prevents overly deep etching when the laser is stationary during direction reversals. The g-code samples provided use negative power values and M4 commands.

To use the g-code generator and create your own customised g-code test patterns:

* download gcmc from vagrearg and unzip somewhere
* download "Etch Test Pattern Generator.gcmc" and "Generate.bat" into the same directory as gcmc
* edit the last line of "Etch Test Pattern Generator.gcmc" as needed
* run "Generate.bat"

## Examples:

Below are examples of painted test tiles etched using this g-code. The first is a red tile painted first with yellow then top coated in white. The second is a yellow tile paint first with blue then top coated in brown. You could just as easily be using the patterns to determine etch density and depth in wood, acrylic or glass.

![20221014_190427 small](https://user-images.githubusercontent.com/7357540/195807971-7a5dc79e-d842-43bb-8d62-ee8ab9bdc0c2.jpg)
![20221014_190454 small](https://user-images.githubusercontent.com/7357540/195808443-a05204f7-d627-4eea-9ae5-0c49cd9e52c6.jpg)

and a sample of what can be done with nearly the right speed/power levels:

![20221014_190515 small](https://user-images.githubusercontent.com/7357540/195808003-41a7fec6-881b-4220-8b38-f8856e8b330f.jpg)

## References:

"gcmc - G-Code Meta Compiler" by Vagrearg at https://www.vagrearg.org/content/gcmc

## Disclaimer

I use the g-code and generator regularly but make no representation of their suitability for your equipment or configuration. Use at your own discretion. I take no responsibility for you, your equipment or the materials you may consume. You MUST verify the g-code is appropriate for your configuration.
