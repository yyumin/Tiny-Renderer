# Tiny Renderer Project
the original project repo: https://github.com/ssloy/tinyrenderer

## Lesson 0: Basic Setup
- **Objective**: Implement functions for drawing line segments and triangles manually.

## Lesson 1: Wire Mesh Rendering
Draw the wire mesh of a three-dimensional model using the Bresenham's Line Drawing Algorithm.

#### Attempt 1
- **Method**: Iterate along the line segment, activating pixels as traversed.
- **Interpolation**: Linear interpolation between a start and end point with a parameter `t` ranging from 0 to 1.
- **Issues**: Limited to 100 steps, resulting in gaps.

#### Attempt 2
- **Step Size**: 1 pixel on the x-axis, then linear interpolation for the y-axis.
- **Issue**: Does not adequately handle steep angles. Creates jagged lines when vertical movement dominates.

#### Attempt 3
- **Solution**: Iterate on the steeper axis. Use the larger delta to define the "X" axis.
- **Adjustments**: Swap x and y if delta y is greater, ensuring progression from low to high values.

#### Attempt 4
- **Optimization**: Factor out repeated calculations.
  - Modify the loop structure.
  - Eliminate linear interpolation calculation.
  - Update the off-axis value if `error` > 0.5.
  - Reset the accumulator using a sliding window technique.

#### Attempt 5
- **Improvement**: Completely remove floating-point calculations.

### Wireframe Rendering
- **Description**: Render the outlines of triangles.
- **Data**: Use `.obj` files, which contain vertex positions and descriptions of faces.

### Lesson 1 Optimization: Reducing Branching
- **Context**: Reduction of branching within loops to prevent pipeline stalls due to branch mispredictions.
- **Advantage**: Enhances runtime efficiency by eliminating the need for the processor to repeatedly evaluate conditional decisions.

### Reference Resources
https://www.youtube.com/watch?v=RGB-wlatStc
- **Bresenham's Line Drawing Algorithm**: Essential for defining lines as a collection of pixels.
- **Rasterization**: The conversion of a vector into a raster format.
- **Sampling Strategy**: Sample more on the axis with higher value density.
- **Floating Point Handling**: Removal of floating point calculations speeds up processing and avoids inaccuracies in integer-based systems.

## Lesson 2: Triangle Rasterization and Back Face Culling
- **Status**: To be continued.
