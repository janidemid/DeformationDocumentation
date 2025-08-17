# Hello!
open LVL_Examples to test plugin out
<img src="Thumbnail3.png">

# How to set up:
  1. Select your mesh material and open it in the material editor.
  
  2. Add a material function and select the collection Deformation function.

  

  3. Use the "getMaterialAttributes" node to get the "normal" and "worldPositionOprion" of function and connect it to normal and worldPositionOffset. If you want to use your own normal map, use "blendAngleCorrectedNormals" to use both.

  4. Place your deformer and add a new item to the "targets" array, then select your target mesh.

  5. If needed, enable physics, either choose a profile or set up your own in the "deformed Physics" tab.

  6. The deformer will automatically pick child scene components of your targets, as well as all blueprint static meshes if the deformer is inside the blueprint.

  7. To make the mesh ignore performers, add an "ignore" tag to the component, or a tag with the name of the performer you want them to ignore.

  8. Strength value defines the privilege of which a performer will have a greater effect if two of them are active in the same area.

  9. "IsDisplacingDeformer" decides whether the deformer will be displacing all inner vertebrae outside the acting licrator.

  you can see how final result should look like here <img src="example.png">
  
## Unfortunately, you have to do this for every material you want to be deformable.

# important functions:
 ### BP_DEFORMER Funciotns:
   -resetDeformer: used to reset static parameters of material, therefore resetting all the deformations by the deformer
   -updateAllStartParameters: Same but will not be adding any new targets
  ### BP_GLOBALDEFORMERSOLVER Funciotns:
   -updateGlobalIds: updating the IDs of deformers. Important if any old deformers were removed or if you have added new targets to the deformer mid-game.
  ### important info:
   -Deformation targets will ignore all the deformation done by deformers whose names are in target component tags. Used for excluding the deformer from deforming one of the meshes inside bp
  The tag "ignore" will make mesh ignorable to deformers of this blueprint.

This plugin consists of a basic deformation system, working by sending real-time data to shaders through material collections and static parameters by rendering target. It can be used to create soft objects like trees, cars etc. or deform static meshes like landscape deformation or realistic destruction.
