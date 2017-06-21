# https://wolfr.am/mAuOX0XK

This repository was made for the Homework Assignment for Wolfram Summer School 2017.
The "FunwithPhysicsin2D.nb" file in this repository contains code for implementing
the steps described in this readme file.

## Motion of a classical particle in a box

Here we will describe the motion of a classical particle inside a box with hard walls.
The particle will be represented by a single unit of a 2D (or 3D) raster. The interactions
with the walls will be considered elastic, i.e. such interactions simply reverse the direction
of motion perpendicular to the wall.

### The first step is to create a box and a point particle with given coordinates within the box.

We first create a 2-dimensional raster with one of the elements highlighted using a different color:
```
mybox[{mx_Integer, ny_Integer}, {px_Integer, qy_Integer}] := 
  Graphics[Raster[
    ReplacePart[
     ConstantArray[{1, 1, 1}, {ny, mx}], {qy, px} -> {1, 0, 0}]], 
   Frame -> True, FrameTicks -> None];
mybox[{20, 10}, {5, 5}]
```
![screenshot](Fig1.png)

### The second step is to animate this box

(Note that the .nb file in this repository has more steps (more detailed description of the process I followed))

```
mytimeAnimatedbox[{mx_Integer, ny_Integer}, {x0_Integer, 
    y0_Integer}, {vx_Integer, vy_Integer}] := 
  Animate[mybox[{mx, ny}, {x0 + vx t, y0 + vy t}], {t, 0, 
    Min[(mx - x0)/vx, (ny - y0)/vy], 1}, AnimationRunning -> False];
mytimeAnimatedbox[{20, 10}, {5, 5}, {1, 1}]
```
![animated_figure](Fig2.gif)

Above we made a 20 x 10 raster in 2 dimensions. The particle is started with coordinates (5,5).
The new function takes values (vx,vy) which describe the speed of the particle in x and y directions respectively.

