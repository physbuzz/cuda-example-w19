Example CUDA project for physics 141/241
===
Updated Feb 4 2019, David Moore.

This code as-is runs an O(n^2) CUDA simulation on 10,000 particles.
Galaxy1.txt is a galaxy of 100,000 particles, and "nSkip" is set to 10 
in kernel.cu, meaning every tenth particle is taken and its mass is multiplied by ten.

Compilation instructions
===

To run, extract all files into a directory. Open up terminal and 
cd into the directory. Then type "make run". This will:
1. Create the "out" directory.
1. Compile kernel.cu into an nbody executable
2. run ./nbody, which outputs 30 .bmp files
3. use convert to put the bitmaps into a .gif


How the source code works:
===

~50 lines of kernel.cu are CUDA code, the rest is C++.
ImageUtil.cpp and ImageUtil.h are some low-quality utilities I wrote for 
outputting images. I do NOT recommend that you use them for your projects, but 
they can be useful for debugging. It's better to plot in matlab or python like usual.

The source code file `kernel.cu` was written while trying to simplify three separate resources:
    1. GPU Gems 3 chapter 21 (the chapter/book is available online)
    2. The CUDA nbody sample project, located on the lab computers at `/Developer/NVIDIA/CUDA-10.0/samples/5_Simulations/nbody/`.
    3. The book CUDA By Example, which I highly recommend.

I also heavily commented the makefile detailing some of its inner workings, so 
please read it if makefiles seem intimidating!

galaxy1.txt is some galaxy with a dark matter halo generated by the Kuijken 
and Dubinski code. The first 50,000 particles are baryonic matter, the second
50,000 are dark matter. Blue particles are Baryonic, red are dark matter.
