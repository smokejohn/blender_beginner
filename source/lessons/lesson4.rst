############################
Lesson 4 - Freeform Modeling
############################
In this lesson we will be mainly talking about **Subdivision Surface Modelling**.
But the Assignment 4 will not use the techniques discusses below. Instead we will
use everything we learned up to lesson 3 to flesh out a concept of a Robot. That
we will later make production ready with the techniques below.

.. image:: ../_static/images/robot_concept.png
   :width: 600


*****************************
Subdivision Surface Modelling
*****************************
To get smooth looking surfaces instead of the faceted or blocky representations
of objects we have been creating until now we can leverage the **Subdivision
Surface Modifier**. The subdivision surface algorithm will create additional
geometry for us, while we only have to edit a simple mesh (often called control cage).


Algorithm - What is happening under the hood
============================================
The subdivision surface algorithm is a recursive algorithm that refines our input
mesh by subdividing it and creating new vertices, edges and faces. Every
implementation of the subdivision surface algorithm has an **Iterations Parameter**
which will enable us to set the number of recursions and create smoother and smoother
looking meshes by subdividing it more and more.

During the refinement stage the shape of our object can change very drastically, we
will discuss ways to control the shape in the section below.

.. figure:: ../_static/images/bl_modifier_subdivisionsurface_cube.gif

    Cube Mesh getting subdivided from 0 to 5 Iterations.

.. warning::
    A big limitation of the Subdivision surface modelling approach is that the algorithm
    only works predictably well on **quadrilaterial faces I.e faces with 4 vertices**.
    Using **triangles or N-gons** will result in **artifacts, bumps and pinches in the
    smoothed surface** and can also lead to the mesh totally losing its form in some places.


Topology for subdivision surfaces
=================================
During the subdivision/refinement the shape of our object can change quite drastically.
How much it changes and which features of the input shape are being smoothed and which
aren't depends on how the mesh is constructed. The structure of a Mesh, I.e how it's
vertices, edges and faces are laid out is often called its **Topology**.

A mesh/control cage that works will with the subdivision surface algorithm has 
good **topology/edgeflow**, I.e the way in which its **edgeloops** and **edgerings** are
laid out create no problems for the subdivsion surface algorithm.

.. figure:: ../_static/images/bl_3dview_subd_topo_example.png
   :figwidth: 600

   Subdivions surface mesh with its control cage edges shown in a smoothed
   **Optimal Display** mode.


Supporting/Holding Edges (Rule of Three)
----------------------------------------
How much the geometry is being smoothed and pulled away from its control cage
depends on how far apart the edges of the control cage are. The farther apart
they are the more smoothing happens and the closer they are the more the 
shape of the control cage stays the same.

For optimal control of each edge in your control cage you want a **supporting
or holding edge** on each side of it. **With this set of 3 edges you can control
how the mesh is getting smoothed on each of the two sides of the edge defining
your base form.** This is sometimes called the **Rule of Three**.

Rule of Three:
    **Have a supporting/holding edge on either side of your form/shape defining edge**

.. figure:: ../_static/images/bl_subd_support_edges.gif

    Simple geometry showing how edge distance changes how the subd-algorithm
    smoothes the mesh.


Working with a support edge on either side of your base or formgiving edge has
other benefits as well. Which we will discuss in the section on `Collapsing/Terminating Edges`_.


Border Edgeloops
----------------
To be able to place supporting or holding edges close to our formgiving/shaping edges we
need to construct our **Edgeloops** and **Edgerings** in a specific manner.
One of those are the socalled **Borderloops**. Borderloops form a loop of connecting
edges that **follow the form of a specific feature we want to cut into our mesh or the
border/outline of our shape**.


.. figure:: ../_static/images/bl_subd_borderloops.png
   
   **Left to right:** Subdivided Mesh, its smoothed (optimal display) and unsmoothed control cage
   with borderloops highlighted in different colors. Every form giving edge als has supporting edges.


Collapsing/Terminating Edges
----------------------------
There will be areas in our mesh where we need more or less edges, so we will
have to get rid of or add in some edges. Because we want our mesh to consist
mostly of quadrilaterials (**Quads**) to prevent problems with the subdivision
surface algorithm we can't just simply remove or add them where/how we want to.

This problem is very common and we have already worked out solutions for most
cases. The graphic below shows the most common termination of edges, but there
will be situations where you will have to improvise and fix your edgeflow
yourself, without any help. The more you model with subdivision surfaces the
better you will get at it.

.. figure:: ../_static/images/bl_subd_quad_termination.png

   3 ways of terminating edges, while keeping everything in quads.


Additional Tools for Subdivions Surface Modelling
=================================================

Remove/Dissolve Edge
--------------------
**Hotkey: Ctrl + X**

The **Dissolve Selection Command** lets you remove edges and their corresponding
vertices quickly. This operation is very useful if you want to change the topology
of your mesh by rerouting some edges.

.. image:: ../_static/images/bl_edit_dissolve_edge.gif

Connect Vertex Path
-------------------
**Hotkey: J**

This tool lets you create a cut between 2 selected vertices. It will use the
shortest path between them to make the cut. This tool is excellent for quick
short cuts for rerouting edgeflow in a mesh.

.. image:: ../_static/images/bl_edit_connect_vert.gif

Shrink/Fatten
-------------
**Hotkey: Alt + S**

Shrink/Fatten moves the selected vertices along their vertex normals and is
a great addition to the normal scale tool. In cases where scaling or moving
of multiple vertices doesn't do the job the **Shrink/Fatten Operator** often
helps a great deal.

.. image:: ../_static/images/bl_edit_shrink_fatten.gif

LoopTools
---------
**Hotkey: RMouse-click (Edit Mode) [After you activated the Addon]**

The LoopTools addon has a range of useful tools that help us to create
shapes in our mesh or help us align a selection of vertices quickly.
Its most useful tool is the **Circle Command** which transforms the elements
of the current selection into a circle.

.. image:: ../_static/images/bl_edit_looptools_circle.gif

You can activate the addon like this:

#. **Edit >> Preferences...** or **Hotkey: F4 >> Preferences...**
#. Open the **Addons** tab on the left hand side
#. Use the **Search textinput** on the top right with the query **loop** to find the addon
#. Activate it by ticking its checkbox

.. image:: ../_static/images/bl_preferences_addons_looptools.png
