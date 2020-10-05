#################################
Lesson 2 - Simple Object Modeling
#################################


**************
What is a Mesh
**************
A polygonal mesh is made up of **vertices, edges and faces**. Together they form a 
3-dimensional solid object with flat polygonal faces, straight edges and sharp corners
(also known as a **polyhedron**). With these basic building blocks it is possible
to create quite complex geometry and there exist algorithms that allow us to subdivide
these meshes into smaller polygons to get very smooth looking surfaces.

.. figure:: ../_static/images/bl_mesh_suzanne.png
   :figwidth: 400

   Example of a polygonal mesh (Suzanne blender primitive)


Vertices, Edges, Faces, Polygons
================================
In blender we have the ability to change the **topology of a mesh** (how the mesh is constructed),
by modifiying its vertices, edges, faces (triangles) or polygons (quadrilaterials and ngons).

.. figure:: ../_static/images/bl_mesh_components.png

   vertices, edges, faces and polygons of a cube


Normals
=======
A normal is a vector that is perpendicular to a given object. In our case there are 
**face normals** and **vertex normals** that are perpendicular to the face or vertex
they originate from. On a 3D mesh **the direction of a normal determines how a polygon
or face is shaded and lit** and because **a face has a front and back, in which
direction the face is pointing**.

.. figure:: ../_static/images/bl_mesh_normals.png
   :figwidth: 400

   3D Sphere with its smoothed normals displayed in pink 


How Normals affect Shading
--------------------------
As mentioned before the normal is used while shading and lighting a 3-dimensional
polygonal mesh. In its simplest form the shading is determined by calculating the
dot-product of the lightvector and the surfacenormal at the shading point. The 
dot-product of two vectors is 1 (Bright/Lit) if the vectors are parallel to each
other (the face is facing the light) and it is 0 (Dark/Shadowed) when the vectors
are perpendicular to each other.

Changing the vertex normals of a 3D plane will change how it is lit and shaded and
might lead to some very weird lighting, as shown in the figure below.

.. figure:: ../_static/images/bl_normals_shading_anim.gif

   3D Plane lit from above getting shaded differently as its normals (pink) are adjusted

We can also use the fact that normals affect the shading of a 3D mesh to our advantage.
By averaging the vertex normals of each face we can fake a smooth surface even though
the mesh consists of flat polygons (The silhouette of the mesh will not improve). 
This method is very prevalent in games and realtime graphics, which makes it possible
to have high fidelity graphics while keeping a lower polygon count.

.. figure:: ../_static/images/bl_mesh_normals_smooth_faceted.png
   :figwidth: 600
   
   3D sphere showing smooth and faceted shading and the underlying normals


**************
Modeling Tools
**************

Add EdgeLoop
============

Knife/Cut
=========

Bevel
=====

Extrude and Inset
=================

Welding
=======
