# Eurobot shared resources

This repository contains a couple of general purpose resources, like the graphics of the playing field, or geometries of the game elements, which we like to share with the public.


## Game Arena

We provide handcrafted SVGs of a flat top-view of the gaming area, which we use in our simulators.
It is handcrafted, so that we can add a lot of metadata into this and use it as a database of game element positions, special areas, etc.
There is a lot of information in the comments of the actual SVGs, so be sure to check out the raw source code as well.

### Coordinate System

The playgrounds use our internal coordinate system, which has its origin at the center of the game area and has the x-axis in parallel to the short side of the game area ("left to right") and the y-axis parallel to the long side ("down to up").

This is a mathematical coordinate system which allows easy mirroring of coordinates *and angles* along the x-axis for easy exploitation of the symmetry of the game arena.
Please note that the y-axis grows "upwards", and not "downwards" as in most graphics coordinate systems.

Therefore to view the field in a modern web browser, please use the `viewer.svg` which does nothing else but translates and scales the `playground.svg` so that you can see it comfortably in your web browser.

### 2.5D Information

SVG does not have a native understanding of 3D coordinates and that's ok, it reduces the geometry complexity tremendously.
However, we do provide z-axis information in our SVGs using tags that are simply ignored by the SVG renderer, but used by our simulator.

The additional tags we introduce are:

- `z`: as the height of the element above the game arena (i.e. the z-axis), *default=0*
- `zheight`: as the dimension of the extrusion of the elements base geometry, *default=0*
- `mobility`: defines the flexibility of movement in all dimensions:
    - `none`: element is fixed (*default*)
    - `rotation`: element can be rotated at its origin around the z-axis only
    - `x` or `y` or `z` or comma-seperated combinations: element can be moved along the x/y/z-axis
    - `any`: element can be moved in all dimension (incl. rotation)
- `movement`: a list of values that can be used to transform this node. Format: `key:min,max`, e.g. `rotate:0,90`

Note that we do not want to build a physics engine with this information (!), but merely do basic collision detection for the robot and its (light/lasor) sensors and allow visualisation of the state of the game elements.

### Game Element Enumeration Scheme

All game elements have a unique identifier which follows an enumeration scheme with the following hierarchy:

1. If element not shared: Ordered by ownership ("ours" vs. "theirs")
2. If (x,y) not unique then first ordered by Z-axis (negative to positive)
3. If (x) not unique then also ordered by Y-axis (negative to positive, "down to up")
4. Otherwise also ordered by X-axis (negative to positive, "left to right")

For most (mobile) game elements the z-axis ordering is not applicable and for many, ordering on the y-axis is enough to identify them uniquely.
Note that the axis ordering information is squashed into a single number!

The naming scheme is `{object}-{owner}?-{number}`, e.g. "seashell-ours-1".

## Contributing

We would love for you to contribute to this effort.
Please fork this repository, commit your changes and create a Pull Request.
Or create an issue, if you found a bug.

Be aware that the techniques and concepts used here may change in the future.

## License

We distribute this under the very permissive 3-clause BSD license. We feel this is appropriate and true to the open nature of the Eurobot competition.
