I purchased this asset in May of 2018 as I am building a VR race game and this asset has terrific options and great frame rate, a necessity for VR development.   However the documentation is minimal and so to get an understanding I wrote this document.  It is just a basic starting point and does not include all of the functionality of this amazing asset.

I have posted this on the Unity Cscape forum and finally thought I should post it here so that others can contribute.

Info by Developer
	• The asset: https://assetstore.unity.com/packages/tools/modeling/cscape-city-system-86716
  • Unity forum for asset: https://forum.unity.com/threads/released-cscape-advanced-building-generator.460380/
  • https://olivrproduction.wordpress.com/cscape-help/ 
	• https://olivr.info/customizing-cscape-materials-with-cdk/
	• IMPORTANT: Review the various Read Me documentation prior to starting.

Videos
	• Create big cities in Unity (with CScape) - General How-To for making a city. https://www.youtube.com/watch?v=jH57G_skl_k&feature=youtu.be
	• CScape 1.0 new features fast tutorial - More recent quick tutorial:  https://www.youtube.com/watch?time_continue=1&v=7t_8Y5GMXnE
	• Main optimizations in CScape 1.0:  https://www.youtube.com/watch?v=zcleFn4fvOM
	• Making a CScape building template: https://www.youtube.com/watch?v=7dhVbB21o9M

I highly recommend creating a testbed application to learn how to use this asset.  Cscape is an impressive application, however because of the large number of capabilities and options you should take some time to learn to use this in a safe and separate project before integrating it into an existing game.
	
	1. Add Cscape asset to game
	2. Add Standard Assets to game (some components used in Cscape)
	3. Add Cscape Toolkit Source:  https://www.dropbox.com/s/8desklhixvtvr6g/CScapeToolsetSources.unitypackage?dl=0
	4. NOT NEEDED  Add https://www.dropbox.com/s/cim4di0xpi53pdn/ShaderPatch2018.0.2f.unitypackage?dl=0
	
Cities can have one or more Districts.  Districts have one or more Prefab (fbx) templates.  Templates are a collection of Facades on a mesh.  

Basic relationship
	○ Cities
		○ Districts
			§ File Location: Assets/Cscape/DistrictTemplates
			§ Prefabs
				□ File Location: Assets/Cscape/Editor/Resources/BuildingTemplates/Buildings
				□ Material: All buildings will use the same Material.  The default Material is MegaCity1
				□ Building Modifier script
					® FAÇADE SHAPE (Façade is spelled wrong all over)
					® Shape: Values 0 to 9  
					® Front Façade Shape.  Don't know what this does
					® Lateral Façade Shape.  Don't know what this does
					® Subdivision Shape.  Don't know
					® Height Subdivision. Don't know
					® Width Subdivision.  Don't know
					® MATERIAL STYLING
					® Façade Material 1 (front/back): Values 0 to 9  - These relate to basecolor_surface_01.png to basecolor_surface_10.png  These images can be found at Assets\CScapeCDK\Editor\Resources\CScapeToolset\Surfaces
					® Façade Material 2 (front/back): Values 0 to 9  
					® Façade Material 1 Lateral: Values 0 to 9
					® Façade Material 2 Lateral: Values 0 to 9 
					® Rooftop Material: Values 0 to 9
			
			
Base Process
	1. Create Facades. Optional
	2. Create Building Templates . Optional
	3. Create Districts.  Optional
	4. Change / Update Textures.  Optional.  A GREAT site for textures:  https://gametextures.com
	5. Create City
	6. Adjust specific buildings

			
Step One: Facades. Optional
	Facades are 2D objects that are templates used by Cscape to make buildings.  There are 40 facades. Each building can have one or more facades.  You can review and change values on the  "Building Modifer" script on each building in a scene.  (Step 6)   
	1. Open the scene CScapeToolkit.  This is found Assets/CScape
	2. Select the "CscapeBaker" in the Hierarchy.
	3. Set the lock icon (upper right) in the inspector so that the Baker does not move away as you adjust windows, etc.
	4. Split your windows so you can see the Game and Scene side-by-side. The Game window will show you a 3D representation of what it will look like. The Scene view is 2D.   Note: In the Scene tab select the "2D" button, near the top left.
	5. Set any of the 40 tiles as desired. (ie: add, remove, move windows and other objects within the Tile. Press the Previous/Next Tile buttons to navigate.
		a.  1 - 21 are façade styles with windows
		b. 22 - 31 are walls
		c. 31 - 34 are ground level facades.
		d. 35 - 40   ???  I, JamesWjRose, do not know
	6. Press the "Bake Textures" button on the SCcape Toolset "CScape Toolset Manager" script
	7. At this point we are done with the CscapeToolkit scene.   Switch back to a game scene, create a new scene if necessary.
	8. If you have not added a "Cscape City" to the scene, do so.  Select the "GameObject" menu, then select the "Cscape" menu, then select "Create MegaCity"
	9. Select the "CScape City" in the Hierarchy
	10. Find the "CS Materials Tools" script attached to the CScape City
	
	
Step Two: Building Templates. Optional
	• Making a CScape building template - Video
	• https://forum.unity.com/threads/released-cscape-advanced-building-generator.460380/page-3#post-3234874
	• If you are using Unity 2018 then make sure to pull down Probuilder 4.x from the Package Manager (Select the Window menu, then select "Package Manager")
	• Pivot point: This is very important.  If the pivot point is not set to the correct corner the layout will be wrong when you apply the mesh.   Here is the details on how to set the pivot point:  Documentation: Element Actions - Center Pivot to Selected Elements
	• To join multiple objects:
		○ Merge and Weld: Unity 3D Probuilder Essentials - Merge and Weld
		○ Select all objects, then from the Probuilder menu select "Merge Objects"

		
Step Three: Create Districts. Optional
	• The included Districts can be found at: Assets\CScape\DistrictTemplates
	• If you want to create your own District select one of the Districts and then press CTRL+D to make a copy.
	• Select "Cscape City" from the Hierarchy
	• Within the "City Randomizer" script there is a "Building Templates" section (3rd section down)   From here you can add, delete or change Districts.
	• Double-Click on the District/Building Template that you want to modify.  From here there are only two options: 
		○ Size: The number of templates available for this district
		○ Elements: Add, delete or change templates

Step Four: Change / Update Textures. Optional
	• There are 21 textures, and there associated Normal, Metallic, Roughness images, can be found at:  Assets\CScapeCDK\Editor\Resources\CScapeToolset\Surfaces
	• "_01" to "_10" are for walls. 
	• "_11 to _21" are for roofs.
	• https://forum.unity.com/threads/released-cscape-advanced-building-generator.460380/page-25#post-4227154
	• Texture size info: https://forum.unity.com/threads/released-cscape-advanced-building-generator.460380/page-24#post-4029151
	• Additional info: https://forum.unity.com/threads/released-cscape-advanced-building-generator.460380/page-2#post-3150851
		○ 1-21 are facade styles with windows
		○ 22-31 are walls
		○ 31-34 are ground level facades
	• Note from the asset author: Facade mat 1 and Facade Mat 2 can be any of the surface textures from range -01 to 10. They are used as combinations. Let's say if 01 is a brick texture, and 05 is a concrete, using Facade mat 1 set to 01, and Façade mat 2 set to 05 will give you façade with combination of those two surfaces. If you invert values, you will have a same combination, but in inverted mode. As for "front" or "side" assignment, you can assign different textures to front/back side of a building. or to lateral sides of a building. (front side is a side that is facing streets).  https://forum.unity.com/threads/released-cscape-advanced-building-generator.460380/page-25#post-4227169
	• TODO: find which items are created and added to the Material.   Currently, when hitting "Compile All Textures" is affecting which files?  It looks like all the files in this folder: Assets\CScape\Editor\Resources\TextureArrays\CScapeToolset are affected and they are added to the Material, right?
		○ Process for creating new city Material:
		○ Make a backup of "Assets\CScapeCDK\Editor\Resources\CScapeToolset\Surfaces"   ie:  "Surfaces - Original Set"
		○ Make a backup of "Assets\CScape\Editor\Resources\TextureArrays\CScapeToolset"  ie: "Array - Original Set" 
		○ Make a duplicate of the "MegaCity1" Material and change the name to something that is more appropriate than "Megacity1 copy"
		○ Change the array images in the Material "MegaCity1" to the array images in "Array - Original Set" (to insure that there is an original set and material
		○ Change images as desired
			§ "_01" to "_10" are for walls. 
			§ "_11" to "_21" are for roofs.
			§ "_31" to "_34" are ground level facades
		○ Select the City in the Hierarchy.
		○ Select the "<todo>" script, and expand the "<todo>" section and change the Material from "Megacity1" to the new material name
		○ Press the "Compile all textures" button
		○ Copy the array images in the: "Assets\CScape\Editor\Resources\TextureArrays\CScapeToolset" folder to a new folder, likely named as the same as the material name.
		○ Open the new material, and change the images in that material to the new folder.
		○ Change the city's material to the new material
	
	
Step Three and/or Four Addendum: Update Textures/Facades. Optional
	• If you have changed templates or textures you NEED to do the following
	• Select "Cscape City" from the Hierarchy
	• Within the Inspector find the "CS Material Tools" script.
	• Press the "Compile only styles" and/or "Compile all textures"

		
Step Five: Create City

• Read the Cscape_Readme.txt file included with the asset.

Step Six: Adjust Individual Buildings

• Select the building you want to change from the scene or via the Hierarchy: Cscape City/Buildings

• Select the "Building Modifier" script.  There are many options to change each building.   (too many for me to document atm)
	
	
