# perceptualdiff (pdiff)
====
a program that compares two images using a perceptually based image metric.

Copyright (C) 2006 Yangli Hector Yee
yeehector@users.sourceforge.net
http://pdiff.sourceforge.net/

This program is free software; you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the
Free Software Foundation; either version 2 of the License,
or (at your option) any later version.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
or FITNESS FOR A PARTICULAR PURPOSE.
See the GNU General Public License for more details in the file gpl.txt.

## Build Instructions

1. Download cross platform make from http://www.cmake.org
2. Download freeimage from https://sourceforge.net/projects/freeimage
3. Edit CMakeLists.txt to tell it where to find your free image build
4. Type `mkdir build; cd build`
5. Type `cmake ..`
6. Type `make .` (or on Windows systems cmake makes a Visual Studio Project file)
7. To build clean, `rm -Rf build` and start again

Note: to specify the install directory, use `make install DESTDIR="/home/me/mydist"`

## Usage

perceptualdiff image1.(tif | png) image2.(tif | png) [options]
-verbose : Turns on verbose mode
-fov deg: field of view, deg, in degrees. Usually between 10.0 to 85.0.
This controls how much of the screen the oberserver is seeing. Front row of
a theatre has a field of view of around 25 degrees. Back row has a field of
 view of around 60 degrees.
-threshold p : Sets the number of pixels, p, to reject. For example if p is
 100, then the test fails if 100 or more pixels are perceptably different.
-gamma g : The gamma to use to convert to RGB linear space. Default is 2.2
-luminance l: The luminance of the display the observer is seeing. Default
 is 100 candela per meter squared
-colorfactor   : How much of color to use, 0.0 to 1.0, 0.0 = ignore color.
-downsample    : How many powers of two to down sample the image.
-output foo.ppm : Saves the difference image to foo.ppm

## Credits

Hector Yee, project administrator and originator - hectorgon.blogspot.com
Scott Corley, for png file IO code
Tobias Sauerwein, for make install, package_source Cmake configuration
Cairo Team for bugfixes
Jim Tilander, Rewrote the IO to use FreeImage.

## Version History

1.0   - Initial distribution
1.0.1 - Fixed off by one convolution error and libpng interface to 1.2.8
1.0.2 - [jt] Converted the loading and saving routines to use FreeImage
1.1 - Added colorfactor and downsample options. Also always output
difference file if requested. Always print out differing pixels even if the test passes.
1.1.1 - Turn off color test in low lighting conditions.

