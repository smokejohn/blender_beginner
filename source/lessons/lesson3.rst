############################
Lesson 3 - Advanced Modeling
############################


********************
Collections / Groups
********************
We can use collection to organize our blender scene and group multiple objects
that belong together. You can navigate your scenes **Collections** in the 
**Outliner** at the top right in the Blender UI. To add objects to a collection
simply **Drag and Drop them onto the Collection in the Outliner**.

To make sure all newly created object are automatically added to the collection
you want **click on the box icon next to the name of the collection to make it
the active collection** (In the image below the *Crate_03* Collection is active)

.. figure:: ../_static/images/bl_gui_outliner_collections.png
   
   Blender outline with the button to create a new collection highlighted in yellow

Blender Manual Link:
    `Blender Manual | Collections <https://docs.blender.org/manual/en/latest/scene_layout/collections/collections.html>`_

**************************************************
Non-destructive / Procedural Modelling (Modifiers)
**************************************************
.. figure:: ../_static/images/bl_gui_modifier_panel.png
   :align: right

   Modifier Panel for a cube object

While all the changes to the mesh we have been doing in edit mode are final
and are hard to change once we exit the modeling tool, there are other ways
to modify geometry that keep the operations adjustable. This way of modelling
is often referred to as **Procedural Modelling** or **Non-destructive Editing**
because we can change the parameters of the modeling operators at any time.

Blender uses **Modifiers** which can be added to objects to implement this
functionality. The |props_modifier| **Modifier Panel** in the **Properties
Panel** on the right hand side of Blenders UI lets you add modifiers to the
currently active object.


.. figure:: ../_static/images/bl_gui_modifier_list.png

   List of all available modifiers in blender

**We will use the following modifiers in this lesson:**

* Mirror
* Boolean
* Solidify
* Bevel
  
.. warning::
    Some modifiers may behave very weird if you have been scaling your objects
    in object mode. That's because their settings sometimes depend on the object
    scale. To prevent unexpected results you should use the **Apply Scale** 
    command to reset the objects scale back to 1.0.

    | **Check object Scale >> 3D Viewport Sidebar (Hotkey: N) >> Item tab >> Scale**
    | **Apply Scale >> Hotkey: Ctrl + A**

    .. image:: ../_static/images/bl_gui_3dview_item.png
    .. image:: ../_static/images/bl_gui_apply_scale.png

Blender Manual Link:
    `Blender Manual | Modifiers <https://docs.blender.org/manual/en/latest/modeling/modifiers/index.html>`_


***************************
Constructive Solid Geometry
***************************
**Constructive Solid Geometry** or **CSG** for short, describes the process of creating
complex geometry from simple solid primitives by subtracting, adding or intersecting
their volumes.
Often this process is called **Booling** or **Boolean operation** because the process
of subtracting, adding or intersecting is often expressed as typical mathematical 
**boolean operations** (NOT, OR, AND, XOR, ...).


In Blender the **CSG/Boolean modifier** features the following boolean operations:

* Difference (Boolean NOT)
* Union (Boolean OR)
* Intersection (Boolean AND)

======================== ============================= ===============================
Boolean Union (**∪**)    Boolean Difference (**-**)    Boolean Intersection (**∩**)
======================== ============================= ===============================
|csg_union|              |csg_difference|              |csg_intersect|
Union of Cube and Sphere Difference of Cube and Sphere Intersection of Cube and Sphere
======================== ============================= ===============================


.. |csg_union| image:: ../_static/images/bl_csg_union.png
    :width: 300
    :alt: Show boolean difference between a 3D Sphere and Cube
.. |csg_difference| image:: ../_static/images/bl_csg_difference.png
    :width: 300
    :alt: Show boolean difference between a 3D Sphere and Cube
.. |csg_intersect| image:: ../_static/images/bl_csg_intersection.png
    :width: 300
    :alt: Show boolean intersection between a 3D Sphere and Cube

With these simple boolean operations it is possible to construct very complicated
geometry while combining very simple building blocks. Multiple CSG operations can
be displayed as a binary tree like in the figure below. The resulting geometry
is shown at the top while it's operands and boolean operations are shown as leaves
(Cylinder, Cube, Sphere) and nodes (Union, Difference, Intersection).

.. figure:: ../_static/images/wikimedia_commons_zottie_csg_tree.png
    :alt: Image showing a binary tree of boolean operations with their operands as leaves
    :width: 600

    Example of complex geometry constructed from simple solid primitives
    (`Wikimeda Commons: Zottie <https://en.wikipedia.org/wiki/Constructive_solid_geometry#/media/File:Csg_tree.png>`_)


How it works in Blender
=======================

Boolean operations are implemented as a blender modifier. The modifier is simply called
**Boolean**.

Here is the step by step process to create a boolean operation between a cube and a sphere:

#. Create a cube (**Shift + A >> Mesh >> Cube**) [Operand A]
#. Create a sphere (**Shift + A >> Mesh >> Sphere**) [Operand B]
#. Select the cube, it will act as our stock (Operand A)
#. | Add a Boolean modifier in the **Modifier Properties** |props_modifier|
   | *The Modifier Properties are located at the right hand side in the* **Properties Panel**

   #. Add the boolean modifier to the cube (**Add Modifier >> Boolean**)
   #. Use the **Object:** Eyedropper tool in the modifier gui to select the sphere as a cutter

      |modifier_panel|
      |boolean_cutter|
#. Select the Sphere in the 3D Viewport and open the **Object Properties** |props_object|
#. Navigate to the **Viewport Display Rollout** and set the spheres display to **Bounds**

   |viewport_display|
#. Now you can manipulate your Sphere (Cutter/Operand B) by selecting its bounds
   and transforming it and the boolean operation will update accordingly.

The result should look something like this:

.. image:: ../_static/images/bl_boolean_cube_sphere.png
    :width: 300

.. |props_modifier| image:: ../_static/images/bl_gui_props_modifier.png
.. |props_object| image:: ../_static/images/bl_gui_props_object.png

.. |modifier_panel| image:: ../_static/images/bl_gui_modifier_panel.png
    :width: 100
.. |boolean_cutter| image:: ../_static/images/bl_modifier_boolean_operand_b.png
    :width: 100

.. |viewport_display| image:: ../_static/images/bl_gui_viewport_display_bounds.png
    :width: 100


A faster and more convenient way to work with booleans
======================================================

There is an addon that ships with blender that makes all of this way easier.
Its called **Bool Tool** and you can find it in the **Preferences >> Add-Ons**.

.. image:: ../_static/images/bl_preferences_addons_booltool.png

After activating the addon you can call it's menu by pressing **Hotkey: Ctrl + Shift + B**

.. image:: ../_static/images/bl_gui_bool_tool.png

The process for booling a cube and a sphere is now way faster and easier:

#. Select the sphere (Operand B / The Cutter)
#. Select the cube (Operand A / The Stock)
#. Press **Ctrl + Shift + B**
#. Select the appropriate boolean operation from the menu

.. note::
    **Brush Boolean** keeps the boolean operation interactive and you can still move
    the cutter while **Auto Boolean** will apply the boolean and only leave the resulting
    mesh behind. Therefore if only choose Auto Boolean if you are sure you don't want
    to tweak the result.
