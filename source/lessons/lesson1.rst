########
Lesson 1
########


*******************************
Viewport Hotkeys and the Numpad
*******************************
A lot of blenders functionality is bound to the number keys on the numpad.
Orthographic views, Isolation mode, Zoom to selected object, are all functions
that are bound to numpad keys.

============ ==========================================================================
Hotkey       Function
============ ==========================================================================
**Numpad 1** Front Orthographic Viewport
**Numpad 2** Rotate Viewport Down
**Numpad 3** Right Orthographic Viewport
**Numpad 4** Rotate Viewport Left
**Numpad 5** Toggle between Perspective and Orthographic Viewport
**Numpad 6** Rotate Viewport Right
**Numpad 7** Top Orthographic Viewport
**Numpad 8** Rotate Viewport Up
**Numpad 9** Toggle Opposing Orthographic Viewport (Top/Bottom, Right/Left, Front/Back)
**Numpad .** Zoom to selected objects
**Numpad /** Isolate selected objects
**Numpad -** Zoom out
**Numpad +** Zoom in
============ ==========================================================================


For Those without Numpads
=========================
Now if you don't have a numpad because you are on a laptop or using a 60% or 80% keyboard,
which are all missing the numpad, you can activate an addon that ships with blender
to access all that functionality via a PIE-Menu.


Activating the Viewport Pie Menu addon
--------------------------------------
* **Edit >> Preferences...** or **F4 >> Preferences...**
* Open the **Add-ons** tab by clicking on it on the left hand side
* Use the search bar on the left to lookg for the **3D Viewport Pie Menus Addon**
* Activate it by ticking on the **checkbox on the left of the Addon Entry**
* Open the Addons Preferences by **clicking on the little triangle arrow left of the checkbox**
* Disable/Uncheck all menus listed in the preferences except the very last one

.. note:: 
    After activating the addon and the **View Numpad Pie** you can call it up around your mouse
    by pressing **[Hotkey: Alt + Q]**

.. image:: ../_static/images/bl_preferences_addons_viewport_pie_numpad.png
    :width: 500
.. image:: ../_static/images/bl_addon_viewport_pie_numpad.png


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
