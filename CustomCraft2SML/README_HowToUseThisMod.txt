How to use CustomCraft2SML (Version 1.10.0)
 -------------------------------------------- 


Custom Craft 2 uses simple text files to send requests to SMLHelper, no coding required
This can be great for those who have a specific ideas in mind for custom crafts but don't have the means to code
Custom Craft 2 is dedicated to Nexus modder Iw23J, creator of the original Custom Craft mod, 
who showed us how much we can empower players to take modding into their own hands
 -------------------------------------------- 


 -------------------------------------------- 
 -------------------------------------------- 
--- Getting Starts ---


 -------------------------------------------- 
Creating the text files that CustomCraft2SML uses can be simple if you're paying attention.
As easy way to get started is to copy the text from the SampleFiles or OriginalRecipes and then modify the parts you want.
When you want to add a new item reference, remember that the 'ItemID' is the internal spawn ID of that item.
    You can visit the Subnautica Wikia for the full list of item IDs at http://subnautica.wikia.com/wiki/Obtainable_Items
The files in OriginalRecipes are generated automatically when the game first loads if the mod detected that they are missing.
    If you can see this file, then the OriginalRecipes will be there.


 -------------------------------------------- 
You'll notice that a lot of text is written between these hash signs (or pound sign or hashtag if you prefer).
Any text in between these symbols is treated as a comment and safely ignored by the mod's text reader.
Use these hash signs if you want to leave notes or comments in the txt files.
Extra whitespace that isn't between quotes (") is also ignored, so feel free to make your files as flat or as indented as you prefer.
It's just recommended that you make them as readable as possible.


 -------------------------------------------- 
Once you've created your txt files, go ahead and launch the game.
Assuming you've got everything configured correctly, your customizations will appear on your next game.
Good luck and happy modding!




 -------------------------------------------- 
 -------------------------------------------- 
--- Working File Types ---


 -------------------------------------------- 
CustomFabricators: Create your own fabricator with your own completely custom crafting tree!
    Custom fabricators have all the same properties as AliasRecipes with the following additions.
    Model: Choose from one of three visual styles for your fabricator.
        Valid options are: Fabricator|MoonPool|Workbench
        This property is optional. Defaults to Fabricator.
    ColorTint: This optional property lets you apply a color tint over your fabricator.
        This value is a list of floating point numbers.
        Use three numbers to set the value as RGB. Example: 1.0, 0.64, 0.0 makes an orange color.
        Use four numbers to set the value as RGBA (RGB with Alpha).
    AllowedInBase: Determines if your fabricator can or can't be built inside a stationary base. 
        This property is optional. Defaults to YES.
    AllowedInCyclops: Determines if your fabricator can or can't be built inside a Cyclops. 
        This property is optional. Defaults to YES.
    Everything to be added to the custom fabricator's crafting tree must be specified as a list inside the custom fabricator entry.
    Every entry will still need to specify a full path that includes the new fabricator as the starting point for the path.
    The lists you can add are as follows.
        CustomCraftingTabs: List of crafting tabs to be added to the custom fabricator.
        AddedRecipes: List of added recipes for the custom fabricator.
        AliasRecipes: List of alias recipes for the custom fabricator.
        MovedRecipes: List of moved recipes for the custom fabricator.
        CustomFoods: List of custom foods for the custom fabricator.


 -------------------------------------------- 
CustomCraftingTabs: Add your own custom tabs into the fabricator crafting trees. 
    An absolute must for organizing large numbers of crafts.
    TabID: This uniquely identifies the tab.
        If you want to use a custom sprite for your tab, the file must be named exactly as the TabID
        This option will take priority over the SpriteItemID.
    DisplayName: The tab name you will see in-game.
    SpriteItemID: Alternative way to set the tab sprite, by re-using the sprite of an existing in-game item.
        This option will be used only if a png file matching the TabID isn't found in the Assets folder.
    ParentTabPath: This defines where your tab begins on the crafting tree.
        You can have as many custom tabs as you want, and even include custom tabs inside other custom tabs.
        Just make sure you add your custom tabs to the file in the correct order, from inside to outside.
        If a custom tab goes inside another custom tab, then the parent tab must be placed above the child tab.
        You can find a full list of all original crafting paths for all the standard fabricators in the OriginalRecipes folder.


 -------------------------------------------- 
AddedRecipes: Adding your own recipes into any of the existing fabricators.
    AddedRecipes have all the same properties as ModifiedRecipes, with the following additions:
    Path: Sets the fabricator and crafting tab where the new recipe will be added.
        Remember, this must be a valid path to an existing tab or to a custom tab you've created.
        You can find a full list of all original crafting paths for all the standard fabricators in the OriginalRecipes folder.
    PdaGroup: Sets the main group for blueprint shown in the PDA.
        This is optional. If PdaGroup is set, PdaCategory must also be set.
    PdaCategory: Sets the category under the group for blueprint shown in the PDA.
        This is optional. If PdaCategory is set, PdaGroup must also be set.


 -------------------------------------------- 
AliasRecipes: A powerful tool with multiple applications.
    Alias recipes allow you to create multiple ways to craft the same item, bypassing one of the limitations of Subnautica's crafting system.
    Alias recipes can also be used to add your own custom items into the game, all without any coding, with some limitations.
    Alias recipes should NOT include an AmountCrafted value. LinkedItemIDs should be used instead to define the produce being crafted.
    AliasRecipes have all the same properties of AddedRecipes, but when creating your own items, you will want to include these new properties:
        DisplayName: Sets the in-game name for the new item.
        Tooltip: Sets the in-game tooltip text whenever you hover over the item.
        FunctionalID: Choose an existing item in the game and clone that item's in-game functions into your custom item.
            Without this property, any user created item will be non-functional in-game, usable as a crafting component but otherwise useful for nothing else.
        SpriteItemID: Use the in-game sprite of an existing item for your custom item.
            This option will be used only if a png file matching the ItemID isn't found in the Assets folder.
            If no file is found with that name, the sprite for the first LinkedItem will be used instead.
            This should only be used with non-modded item values.


 -------------------------------------------- 
ModifiedRecipes: Modify an existing crafting recipe. 
    Ingredients: Completely replace a recipe's required ingredients.
        This is optional if you don't want to change the required ingredients.
    AmountCrafted: Change how many copies of the item are created when you craft the recipe.
        This is optional if you don't want to change how many copies of the item are created at once.
    LinkedItemIDs: Add or modify the linked items that are created when the recipe is crafted.
        This is optional if you don't want to change what items are crafted with this one.
    Unlocks: Set other recipes to be unlocked when you analyze or craft this one.
        This is optional if you don't want to change what gets unlocked when you scan or craft this item.
    ForceUnlockAtStart: You can also set if this recipe should be unlocked at the start or not. Make sure you have a recipe unlocking this one.
        This is optional. For Added Recipes, this defaults to 'YES'.
    UnlockedBy: Set this recipe to be unlocked when any one of the items listed here gets unlocked.
        This is optional. If this is for an existing recipe, note that the original unlocks will not be affected.


 -------------------------------------------- 
CustomFoods: A powerful tool to satisfy the insatiable.
    Custom foods allow you to create custom eatables, for example Hamburgers or Sodas.
    CustomFoods have all the same properties of AliasRecipes, but when creating your own items, you will want to include these new properties:
        FoodValue: Defines how much food the user will gain on consumption.
            Must be between -99 and 100.
        WaterValue: Defines how much water the user will gain on consumption.
            Must be between -99 and 100.
        DecayRateMod: An optional property that defines the speed at which food will decompose.
            If set to 1 it will decompose as fast as any cooked fish.            If set to 2 it will decay twice as fast.
            If set to 0.5 it will decay half as fast.
            And if set to 0 it will not decay.
            Without this property, the food item will not decay.
        FoodType: Sets the model the food should use in the fabricator and upon being dropped. This needs to be an already existing food or drink.
            Leaving out this property results in an automatic definition based on the food and water values.
        UseDrinkSound: An optional property that sets whether the drinking sound effect should be used when consuming this item.
            Set to 'NO' to force the eating sound to be used, regardless of the WaterValue.
            Set to 'YES' to force the drinking sound to be used, regardless of the FoodValue.
            If not set, then the drinking sound will be used if WaterValue is 5 times greater than FoodValue


 -------------------------------------------- 
MovedRecipes: Further customize the crafting tree to your liking.
    All moved recipes work with existing crafting nodes. So all moved recipe entries should be for items that can already be crafted.
    OldPath: If you want to move a craft node from its original location, this must be set.
    OldPath: If you want to move a craft node from its original location, this must be set.
        This node is optional if Copied is set to 'YES'.
        This node must be present if Hidden is set to 'YES'.
        This cannot be used to access paths in modded or custom fabricators.
    NewPath: If you want to move or copy the recipe to a new location, set the path here. It could even be a different (non-custom) crafting tree.
        This node is optional if Hidden is set to 'YES'.
        This node must be present if Copied is set to 'YES'.
        if neither Copied or Hidden are present, then the recipe will be removed from the OldPath and added to the NewPath.
    Copied: If you want, you can copy the recipe to the new path without removing the original by setting this to 'YES'.
        This node is optional and will default to 'NO' when not present.
        Copied cannot be set to 'YES' if Hidden is also set to 'YES'.
        Moved recipes will be handled after all other crafts, so if you added a new recipe, you can copy it to more than one fabricator.
    Hidden: Or you can set this property to 'YES' to simply remove the crafting node instead.
        This node is optional and will default to 'NO' when not present.
        Hidden cannot be set to 'YES' if Copied is also set to 'YES'.
    Remember, all paths must be valid and point to existing tab or to a custom tab you've created.
    You can find a full list of all original crafting paths for all the standard fabricators in the OriginalRecipes folder.


 -------------------------------------------- 
CustomFragmentCounts: Change how many fragments must be scanned to unlock recipes/blueprints
    In addition to the usual ItemID, you only need one more property for this one:
        FragmentsToScan: Simply set this to the total number of fragments that must be scanned to unlock the item in question.


 -------------------------------------------- 
CustomSizes: Customize the space occupied by an inventory item.
    Width: Must be a value between 1 and 6
    Height: Must be a value between 1 and 6


 -------------------------------------------- 
CustomBioFuels: Customize the energy values of items in the BioReactor. 
    Energy: Set this to the amount of energy the item provides via the BioReactor
    This can also be used to make items compatible with the BioReactor that originally weren't.




 -------------------------------------------- 
 -------------------------------------------- 
--- Change Log ---


 -------------------------------------------- 


Version 1.9 makes changes to CustomFoods
AllowOverfill has been removed from CustomFoods as it is no longer enabled by the game
Added UseDrinkSound as a YES/NO entry so that the drinking sound effect is used over the eat sound effect
Corrections made to the documentation of Custom tabs and BioFuel
 -------------------------------------------- 
Version 1.8 adds the long awaited custom foods
You can now create foods with custom food and water values and change the speed of decomposition for your foods.
Additionally you can change the model your item uses to already existing foods, for example a Cooked Peeper, otherwise it will auto-select using the food and water values.
CustomFoods are available in the CustomFabricators too.


 -------------------------------------------- 
Version 1.7 adds some very big additions to really help make your crafting.
You can now make your own Custom Fabricators and set up your own crafting tree in them from scratch.
MovedRecipes can now copy an existing crafting node into another fabricator, even a custom one, without removing the original.
Everything that derives from ModifiedRecipes (which includes AddedRecipes, AliasRecipes, and now CustomFabricators) now has the 'UnlockedBy' property.
UnlockedBy lets you specify a list of TechTypes that will be updated to unlock your main item whenever you discover any of those.


 -------------------------------------------- 
As of version 1.6, introduces powerful tools that let you further create your own crafting experience.
AliasRecipes receive the new FunctionalityI, letting these items use in-game model while crafting and even mimic their in-game functions.
MovedRecipes now let you move things around the crafting tree, or start removing parts of it entirely.


 -------------------------------------------- 
As of version 1.5, you can include modded items in your custom crafts.
Most modded items should work, but we can only guarantee compatibility with items created using SMLHelper.
To get the ItemID for modded items, consult with the original mod author.


 -------------------------------------------- 
Additional features may be added in the future so keep an eye on the Nexus mod page.
After an update, this file will be updated with new info the next time you load the game.


 -------------------------------------------- 
As of version 1.2, file names no longer matter. All files in the WorkingFiles folder will be read and parsed into the game. So name them however you want.
If you want to be able to easily sahre your custom crafts with others, make sure to chose unique names for your files.
Remember: For now, each file can only contain one type of entry. The valid entry types are: MovedRecipes, CustomSizes, CustomBioFuels, CustomCraftingTabs, ModifiedRecipes, AddedRecipes, AliasRecipe.




