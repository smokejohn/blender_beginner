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
**Switch between Edit and Object Mode | Hotkey: Tab**

To access the modeling tools and be able to change the topology of the active objects
mesh data we have to switch from **Object Mode to Edit Mode** you can do that by
pressing **Hotkey: Tab** or by using the **object interaction mode dropdown** in
the top left corner of the **3D Viewport**. Now you can access all of blenders
mesh editing tools, some of which are described below. Once you are done editing
the mesh you can press **Hotkey: Tab** again to go back to **Object Mode**.


.. image:: ../_static/images/bl_gui_3d_view_object_interaction.png


Loop Cut and Slide
==================
**Hotkey: Ctrl + R**

The Loop Cut tool is a great tool to add additional edges that follow the current topology.
It uses the concept of edge and face loops to determine where to cut and gives you the
ability to slide the new edge loop around before inserting it. More information on the
Loop Cut tool and what exactly face and edge loops are can be found by following the
links to the blender manual below.

.. image:: ../_static/images/bl_edit_loop_cut.gif

Blender Manual Link:
    `Blender Manual | Loop Cut <https://docs.blender.org/manual/en/latest/modeling/meshes/tools/loop.html>`_
    `Blender Manual | Select Loops <https://docs.blender.org/manual/en/latest/modeling/meshes/selecting/loops.html>`_


Knife/Cut
=========
**Hotkey: K**

The Knife tool is great for cutting arbitrary shapes into the existing geometry.
After you have set your cut by left clicking repeatedly confirm the cut by pressing Return/Enter.

.. image:: ../_static/images/bl_edit_knife.gif

Blender Manual Link:
    `Blender Manual | Knife <https://docs.blender.org/manual/en/latest/modeling/meshes/tools/knife.html>`_

    
Bevel
=====
**Hotkey: Ctrl + B**

The Edge Bevel Tool allows you to round of edges or chamfer them. It's one of
the best tools for smoothing out the very harsh and unnatural edges of our meshes.

.. image:: ../_static/images/bl_edit_bevel.gif

Blender Manual Link:
    `Blender Manual | Bevel <https://docs.blender.org/manual/en/latest/modeling/meshes/editing/edge/bevel.html>`_


Extrude and Inset
=================
| **Extrude | Hotkey: E**
| **Inset | Hotkey: I**

Extruding is one of the main ways to add geometry and simultaneously grow our object/mesh
into a direction, it works on all mesh components (vertex, edge, face).

Inset is a great to to create slots or prepare geomtry for extrusion. It's also one
of the tools that will be very useful later on when we look at subdivision surface
modeling.

.. image:: ../_static/images/bl_edit_extrude.gif
.. image:: ../_static/images/bl_edit_inset.gif

Blender Manual Link:
    * `Blender Manual | Extrude <https://docs.blender.org/manual/en/latest/modeling/meshes/tools/extrude_region.html>`_
    * `Blender Manual | Inset <https://docs.blender.org/manual/en/latest/modeling/meshes/editing/face/inset_faces.html>`_

Deleting and Welding/Merge
==========================
| **Deleting Geometry | Hotkey: X**
| **Welding/Merging | Hotkey: M**

We can also simply delete components of the mesh (vertex, edge, face) to create
holes or prepare the geomtry for other operations by pressing **Hotkey: X**

Sometimes we have holes in our meshes or wish to merge together vertices to create
spikes or other shapes. The Merge tools let you close meshes or weld together vertices
into a single vertex.

.. image:: ../_static/images/bl_edit_weld.gif

Blender Manual Link:
    `Blender Manual | Merge <https://docs.blender.org/manual/en/latest/modeling/meshes/editing/mesh/merge.html>`_
