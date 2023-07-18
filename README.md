# HoudiniMeshPatchDeformers
simple houdini node stack setups for character blendshapes. useful for bodies and face meshes

## simple install
add the 2 HDA files to your "C:\Users\username\Documents\houdini19.5\OTLS" folder
I haven't tested any other versions except 19.5.
test Patch_deform_samples file

## demo vid
https://miro.com/app/board/uXjVM2iuRv4=/?share_link_id=444239530165
Presentation link for 

## PatchBlend hdalc
mesh needs to have non-overlapping UVs in the vertex attribute (I dunno how to make it show an error to enforce it on meshes that have UV on points)
used for blending a patch of polygons to a more complete mesh. 

input 1 - Original Mesh (put the core mesh here)
input 2 - Patch Mesh (put the modified patch mesh here)
output1 - final mesh with patch blended into it

Blend - move this to blend between the original mesh and the mesh with the patch blended in
Blur Inside - the inner patch polys deltamushed
Blur Outside - the outer patch polys deltamushed


## Patchrig hdalc
used to add a simple kinefx rig to a selection of polygons, can be used with patch blend to make some blendshapes easily for meshes. this is an HDA where the 2nd and 3rd output can feedback into the 2nd and 3rd port on the input.


input 1 - mesh - original mesh, default settings will blast out the polys to mod
input 2 - custom edit bind Step 2
input 3 - rig pose step2

output1 - bone deformed mesh 
output2 - custom edit bind Step 1 (pipe this into a rig pose or edit, before piping back into the 2nd input port)
output3 - rig pose Step 1 (pipe this to a rig pose or edit, before piping back into the 3rd input port)

Process - default is off, once you switch this on, the kinefx rig will process, can take time depending on your settings.
use custom edited bind - using this allows you to modify the bind bone positions, useful with convex tet hull setting ON
update normal - use normal with 60 at the end
use convex hull - puts a hull around the whole object before doing a tet mesh
use original mesh - if this is off, the selected 'polys to mod' will be the output mesh, if turned on, it will export the whole original mesh deformed

Polys to mod - you can select which parts of the mesh actually get processed
polys to rig - select polygons to use as points for kinefx bone rig

