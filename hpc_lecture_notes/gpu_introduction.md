# An Introduction to GPU Computing

## Background

Graphics Processing Units (GPUs) are extremely powerful compute
devices. To understand where GPUs are coming from, consider a three
dimensional scene. Typically, three dimensional objects are
constructed from a large number of flat surface triangles with
coordinates $(x_i, y_i, z_i)$. Now imagine a camera that is moving
through the room. In order to display a 2-dimensional image, for each
triangle we need to compute the projection onto the two dimensional
viewing plane represented through the camera parameters. In addition,
we need to deal with surface textures, light sources and computations
which triangles are visible and which aren't. This is a huge number of
operations that can be done independently for each triangle. GPUs have
been designed to perform these highly parallel operations extremely
fast. The secret is that GPUs consist of a large number of very simple
processing units that are optimised to do these very simple operations
but are inefficient for complex operations such as branching.

In the early two thousands it was first recognized that GPUs may be able to be used to accelerate mathematical algorithms other than graphics calculations. In particular, if we have a large number of independent operations on highly structured data, GPUs can give significant performance benefits compared to CPUs. However, not all types of computations can benefit from GPU acceleration. Examples include:

* Highly serial algorithms. If there is no inherent parallelism, a GPU won't help much. CPUs are much better devices for single threaded applications than individual GPU processing units.
* Strongly memory bound computations. If we have large amounts of data but very little to do per data unit, a GPU may not be well suited. We need to transfer the data to the compute device, which for discrete accelerators means system bus transfers that are slow compared to direct communication between CPU and memory. We may interleave memory operations and computations. But this only works well have the computational load is sufficiently high. Some modern integrated CPU/GPU architectures share the RAM. For these such considerations are less relevant.


