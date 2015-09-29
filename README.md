# Eurobot shared resources

This repository contains a couple of general purpose resources, like the graphics of the playing field, or geometries of the game elements, which we like to share with the public.


## Playgrounds

We provide handcrafted SVGs of a flat top-view of the gaming area, which we use in our simulators.
It is handcrafted, so that we can add a lot of metadata into this and use it as a database of game element positions, special areas, etc.

It also uses our internal coordinate system, which has its origin at the center of the game area and has the x-axis in parallel to the short side of the game area ("left to right") and the y-axis parallel to the long side ("down to up").
This is a mathematical coordinate system which allows easy mirroring of coordinates *and angles* along the x-axis for easy symmetry of game area.
Please note that the y-axis grows "upwards", and not "downwards" as in most graphics coordinate systems.

Therefore to view the field in a modern web browser, please use the `viewer.svg` which does nothing else, but rotate, flip, translate and scale the `playground.svg` so that you can see it normally in your web browser.


## Contributing

We would love for you to contribute to this effort.
Please fork this repository, commit your changes and create a Pull Request.
Or create an issue, if you found a bug.


## License

We distribute this under the very permissive 3-clause BSD license. We feel this is appropriate and true to the open nature of the Eurobot competition.
