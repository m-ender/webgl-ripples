WebGL Ripples
=============

A physically realistic real-time simulation of (transversal) 2D waves in WebGL.

[Check out the live demo!](http://mbuettner.github.io/webgl-ripples)


Technical Details
=================

The waves are simulated on a square grid in the form of a texture on the GPU. Each frame, the texture is updated based on the last two frames. Then this texture is used in a second pass to create a simple rendering (using surface normals for specular lighting).

`bcTexture.png` is loaded to provide "boundary conditions" (regions where the amplitude of the wave is always zero), by reading its alpha channel.

The simulation is done by solving the [wave equation](https://en.wikipedia.org/wiki/Wave_equation) with a simple explicit finite-difference scheme of 2nd order.

New waves are created by writing a small sinusoidal ripple into the last two frames (the second one slightly larger than the first) before calculating the next frame.
