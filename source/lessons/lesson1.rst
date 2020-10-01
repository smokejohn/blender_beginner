#####################
Lesson 1 - Primitives
#####################

The goal of this lesson is to create a cyberpunk/scifi city block by arranging simple primitives.
Basic Material creation and assignment to the primitives and simple lighting are also part of this
exercise. The result should come somewhat close to the example below.

Exercise Naming Convention
    | Name every file you turn in for the assignment with the following naming convention:
    | **lesson1_firstname_lastname.ext** (where .ext is the file extension e.g. .jpg, .png, .blend)

Exercise submission:
    * **Full HD Render 1920x1080 (Eevee)**
    * **.blend-file**


***********************************
Selection, Duplication and Snapping
***********************************


Selection
=========
| Object selection is explained very well in the official blender manual so refer to it for a detailed explanation. 
| Here is a short table to get you started on the basics.

=========================== ==========================================
Hotkey                      Function
=========================== ==========================================
**LMouse**                  Select an object
**Shift + LMouse**          Add or remove object from selection
**Ctrl + LMouse-BoxSelect** Remove box selected objects from selection
=========================== ==========================================

Blender Manual Link:
    `Blender Manual | Selecting <https://docs.blender.org/manual/en/latest/interface/selecting.html>`_


Active Object
-------------
The active object is the object which properties are displayed in the **Properties Panel**.
It is often the last selected object, which makes selection order important because many
operators pay special attention to the active object versus the other selected objects.

Duplication
===========
To duplicate the seleced object simply press **Shift + D**. Blender will duplicate all
selected objects and put you into the gizmoless Move/Grab Object(s) mode where you can either
place the object(s) where you want or cancel the transformation by clicking **RightMouse-Button**.
The duplicate object will then be in the same position as the original and overlap it.

For more information please refer to the official blender manual:

Blender Manual Link:
    `Blender Manual | Duplicate <https://docs.blender.org/manual/en/latest/scene_layout/object/editing/duplicate.html>`_


Snapping
========
Snapping helps you place an object more accurately by automatically aligning object features
to each other. The Blender manual is very thorough on this topic and explains it very well.

============================= ==============================================================
Hotkey                        Function
============================= ==============================================================
**Ctrl** (while transforming) Holding down Ctrl enables snapping until you release it again
**Shift + Tab**               Enables or Disables Snapping globally
**Ctrl + Shift + Tab**        Opens the Snap settings as a floating panel next to your mouse
============================= ==============================================================

Blender Manual Link:
    `Blender Manual | Snapping <https://docs.blender.org/manual/en/latest/editors/3dview/controls/snapping.html>`_
