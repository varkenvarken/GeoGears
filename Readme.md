# GeoGears

The first result of my journey into geometry nodes, licensed as Creative Commons CC-BY-SA-4.0

It was quite the learning curve to be honest, even though I have a fair bit of
[experience as an add-on programmer](https://blendermarket.com/creators/varkenvarken).

Nevertheless, it is fun to do, and although I am not done yet with the node setup,
I started documenting it on [my blog](https://blog.michelanders.nl/).

It is also fairly well documented in the nodes setup itself.

## usage

The file [GeoGears.blend] contains a geometry node called `Gear`.

- add any mesh object to your scene,
- switch to the Geometry Nodes layout and
- in the Geometry Nodes Editor, click on the dropdown left of the New button
- select `Gear`

The node will appear in the Modifier panel of the Properties where you can change the parameters.

## parameters

### main modeling parameters

- Module

    the distance between two teeth

- Teeth

    the number of teeth on the gear. The circumference of the gear at its pitch circle will be module * teeth

- Pressure angle

    The tangent of the tooth profile at the pitch point. typically 20 degrees for modern gears and 14.5 for old gears

- Helical angle

    The amount in degrees that the top side of the gear is rotated relative to its bottom side.

- Bevel angle

    The amount in degrees that the teeth are angled. Two gears with a 45 degree bevel angle can be meshed perpendicular to each other

- Thickness

    distance between to top and bottom sides of the gear

- Clearance

    the extra amount of space below the dedendum circle as a percentage of the module. Necessary to prevent to tips of the teeth hit the bottom land of the other gear.

- Center radius

    radius of the hole through the center. Cannot be zero at the moment.

### the Presentation panel

Allows some control of the quality of the generated mesh and the way it might be rendered.

- Tooth profile resolution

number of points used to generate the involute profile of a tooth. The final number is less because the profile will be truncated at the addendum. More is smoother

- Root profile resolution

number of points used to generate the root profile (or 'bottom land'). More is smoother (more circular)

- Name of generated UVmap

Choose anything you like

- Sharpness angle

edges this ahrp or sharper will be marked as a seam

- Material

the material to apply to the generated mesh

### visualization

To allow to visialize the radii of several important construction circles, you can toggle those on and off. The Pitch Circle is the most interesting one because the gears will mesh best when their pitch circles touch.


## reference

See [Wikipedia Gear](https://en.wikipedia.org/wiki/Gear), in particular the section on [nomenclature](https://en.wikipedia.org/wiki/Gear#Nomenclature).

## caveats & known problems

This is a work in progress, breaking changes may be implemented in the future.

Also, this is *not* an engineering implementation: the involute profile is accurate but things like undercut etc. are *not* addressed. Also, the mesh might not be water tight, so you probably shouldn´t use it for 3d printing, but your mileage may vary.

Currently, under some combinations of module, teeth and bevel angle, some faces may disappear. I hope to fix that in a future version.

## acknowledgements and attributions

See the file [Acknowledgements] for the textures used in the examples.
