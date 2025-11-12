# Mesh Generation Python Package

### Project Overview
This project was developed during my Summer 2025 internship at Los Alamos National Laboratory (LANL). I worked in the EES-17 National Security Earth Science group where I helped develop an image-based grain partitioning and multi-phase numerical mesh generation Python package. This package is intended as a tool to produce numerical meshes for finite element modeling used in geomechanics and computational physics reaserach.

- The open-source package is available at: https://github.com/cjohnson-LANL/grain2mesh-main
- SoftwareX manuscript: https://www.sciencedirect.com/science/article/pii/S2352711025003930

### Motivation
Exisiting image-based mesh generation software typically lack crucial preprocessing steps that ensure the generation of a high fideltiy mesh ready for use in computational mechanics solvers. Our package, grain2mesh, combines image processing and mesh generation into a single package that allows users to easily generate the meshes they need for modeling and simulation.


### Contributions
My main responsibilty was to finalize an existing workflow and develop and modular package that can easily be expanded upon by future contributors. I was involved in the architecure design of the package as well as testing and implementation. I am also a co-author of an accompanying manuscript to be published in the December 2025 edition of SoftwareX.



## System Architecture
The Grain2Mesh software package runs a 6-step image processing and mesh generation pipeline that allows users to generate simulation ready meshes from grain images. Details of the pipeline are listed below.

### Image Processing Pipeline
1. Filtering & Segmentation
   - Raw input images are first filtered to reduce noise and small features that can disrupt the mesh generation
   - Grains are segmented using either watershed segmentation or an integrated convolutional neural network (CNN) depending on the input image and user configuration
  
2. Grain Labeling
   - Individual grains and pore spaces are labeled so they can be assigned unique material properties in later stages
  
3. Creating Polygon Surface
   - The filtered and labeled image is used to construct a polygon surface pixel by pixel 
  
4. Constructing Cubit Surface
   - The polygon surface is reconstructed in Cubit (a mesh generation software) where it can be further processed to generate a numerical mesh
  
5. Edge Splining
   - The edges between grains are smoothed using spline interpolation to ensure a topologically consistent geometry
  
6. Final Mesh Generation
   - A final numerical mesh is generated from the processed surfaces that allows users to add boundary conditions as they see fit for their model


<br>

![Example Workflow](/Fig1.jpg)

*Example workflow using micro-CT scan of Berea Sandstone*
