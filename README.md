# rgb8bit

This mod provides a new color palette for use with hardware coloring in Minetest. 256 colors are specified from a combination of 3-bit red values, 3-bit green values, and 2-bit blue values. Helper functions are provided to quantize your RGB values given a value range. 

## Credit
[Prof. Paul Pickell](https://github.com/pauldpickell) (University of British Columbia) implemented the palettes in 8-bit (256 colors) as an installable mod for Minetest.

## Install the palettes
Unpackage the `rgb8bit` folder into your mod directory, located where ever you installed Minetest.

## Use
`rgb8bit` utilizes [hardware coloring](https://minetest.gitlab.io/minetest/textures/#hardware-coloring) and supports passing a `param2` value to a `rgb8bit` node. The mod only registers the 8-bit palette, which is meant to be used in conjunction with RGB values that will color the node with other mods.

### Example using 8-bit RGB values quantized with a range of 0 to 255
```
-- Quantize RGB values
local red = rgb8bit.map_value_to_3_bits(input_red_value, 0, 255)
local green = rgb8bit.map_value_to_3_bits(input_green_value, 0, 255)
local blue = rgb8bit.map_value_to_2_bits(input_blue_value, 0, 255)

-- Get the index of the color from the palette
local color_index = rgb8bit.get_palette_index_from_rgb(red, green, blue)

-- Write the quantized values to the param2 value and assign the rgb8bit node to the data
data[vi] = minetest.get_content_id("rgb8bit:rgb8bit")
param2[vi] = color_index
```
