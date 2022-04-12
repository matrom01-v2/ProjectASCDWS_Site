# Project Design

## Brief Key Architectural Drivers
> ### The Why

For figuring out what we needed for our architecture, we first needed to know how this game was going to be played, accessed and used. With this in mind, our game is a singleplayer game with no real need to access any outside information other than your saves and the game data. This would allow us to use a more secluded architecture that could be downloaded and work independently from any other systems.

We would need the game to be able to respond to updates in the system. This includes entering new areas, inventory systems, saved data, NPC interaction, and the combat system. Our code is currently based on classes. This means that every  component is coded separately but they are also able to easily interact with each other. An example of this is our collidable class and NPCs/Player classes. These classes are able to interact to centralize reusable code.

---

## Blackboard Architecture
> ### The How

![ARCHITECTURE DRAWING](https://user-images.githubusercontent.com/90274287/161161066-57d9bf90-0e91-4b86-8368-7f872e60ff9b.png)

This architecture helps in quick read and write access for all elements within the game with a singleton instance, our "BlackBoard," called the GameManager.

Key important pieces to our game's architecture, such as the Player framework, Story Manager, Boss Framework, and Level Manager, all need access to each other's data and states. Rather than importing each and creating and linking multiple different references to each new item that we need - I.E. in Player, make a reference to Story Manager, Level Manager, and Boss - even if we might need it for only one miniscule piece in our code, we can make one link to the Blackboard, and a link back.

By making a link to the BlackBoard to access its components, and a link referencing back to the original piece (Player, Story, Level, Boss), and doing the same for every single class that needs to access others, we can have a two-way pipeline that allows for only one reference being needed.

Gone are five different references; one holds them all. This also helps if later in our design we split the Story Manager into different pieces rather than just one piece, or if we develop cutscenes, we can set the "inCutscene" flag to true, and any key items that only work when not in a cutscene will automatically be informed of it instead of having to reference yet another class specifically for cutscenes.

### Risks

We do acknowledge the risks of singleton classes, especially syncronization issues. If we have any classes or updates that need to be made to our singleton Game Manager, we will need to create specific locks (blocks) to prevent any changes to specific items that could be overwritten by other classes that also write to the blackboard in order to keep everything syncronized, and there is no possibility for a segmentation fault, invalid data access, or corruption. For example, if the game is being saved during a quicksave or full save, we want to lock all changes incoming, which could be done by setting a "lock" flag to true, and all setters need to have an additional check for a lock and hold the change in a queue.

### Examples

Certain interactions need access from other pieces in our framework. For example, in the purple highlight, Level needs the information on which boss is needed, which then gives the Boss Manager the necessary level information to give a random boss for the current level. Once the boss is generated and returned, possibly with a `generateBoss(current_level)` function, the level can then generate the appropriate room and spawns, then save its data into the Blackboard. The purple lines are "pseudo" lines, and show an example relationship, but all of this occurs through the "middleman" which is the Blackboard.

Pronouns are another good example. Via player preference, we can set the pronouns that the player wishes to be referred to in-game by NPCs, the narrator, or any other necessary text menu or popup, which can be in a variety of different classes that need access to that preference. By centralizing it within the BlackBoard, each class that needs access to it can simply call the C# getter (which is just the capital version of the property) for Subjective, Objective, and Possessive, whenever a pronoun is needed. The boss could be referring to the player, or the story manager could be displaying a series of text menus or cutscene dialogues, or an NPC could be referring to the player via pronouns. All player preferences live in the Blackboard.

---

## Singleton Blackboard
> ### Meet: The GameManager

---

## Game Objects and Scripts
---

These are scripts attached to objects that extend from the `MonoBehavior` class. The scripts enact certain actions and functionality for objects such as the player and NPCs.

### Item Database (`ItemDatabase.cs`)
---
Item database stores all instances of unique items to be quickly referenced and copied into the player's inventory.


### Player Inventory (`InventoryManager.cs`)
---

---

## Static Classes
---
These classes do not extend Unity's `MonoBehavior` class, and are used in conjuction with scripts that do. These are helpers to encapsulate key data points such as Items and their information.

### Item (`Item.cs`)
---
This is a Static class for all in-game items.
- Items can have an ID, name, description, weight, an icon for the inventory, and any extra stats that might come in handy for later development stages.
- These items are disconnected from Unity's MonoBehavior library and are addons to an item that uses the `Pickup.cs` script, or are located within any objects that are Collectables (`Colletable.cs`).
- Item icons are stored in the following directory relative from root **AND ARE TO BE NAMED EXACTLY AS THE ITEM IS NAMED IN-GAME**:
```
/Sprites/Items
Convention example:
-----------------------
Directory: /Sprites/Items/Blue Key.imageExtension
Item instance: {
name: "Blue Key"
}
```

This is due to the Item class constructor using the `itemName` property to fetch and Reload the icon for later use in the project.

UML DIAGRAM
```
Item {
public
------
Constructor(
	id : int,
	weight : int,
	name : string,
	description : string,
	stats : dictionary<string, int>
) : Item
Constructor(Item item) : Item
itemId     : int
itemName   : string
itemDescription : string
itemWeight : int
itemIcon   : Sprite
stats      : Dictionary<string, int>
}
```

---