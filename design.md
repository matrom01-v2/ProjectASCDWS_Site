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

The GameManager.cs file is the file that tends to work as a hub for the rest of the files. Examples of this currently are the Awake, ShowText, the prononouns, SaveState, and LoadState methods which is used once the game starts. 

- Awake Method
	- The awake method is used once the game has been launched and is used to create a screen resolution, create an instance of GameManager, loads the load state if there is any, and creates an object to not destroy.
- Pronouns
	- These pronouns are going to be used for player preference. This is part of our customizability that will let the player work with their preferences in game.
- Subjective/Objective/Possesive Methods
	- This method will return the type of pronoun from the lists created to be used in text labels later on throughout the story.
- ShowText Method 
	- This method is called to be able to show a floating text in the game. If we want something to pop up when there is an interaction, such as walking into a chest or talking to an npc, this method will be called to show the text on the screen for a chosen amount of time with specific font size, color, position, and motion.
- SaveState method
	- This method will load the current save state of the game and set it.
- LoadState method
	- Checks if there is a current savestate and will load that save state into the game if there currently is one, otherwise will do nothing.

We also create certain objects for use later in other methods as well. Examples of these are the:
- Player object
- FloatingTextManager object
- PlayerSprites 
- WeaponSprites 
- itemDataBase

---

## Game Objects and Scripts
---

These are scripts attached to objects that extend from the `MonoBehavior` class. The scripts enact certain actions and functionality for objects such as the player and NPCs.

### Movement (`Movement.cs`)
---
This class handles all movement behavior, which includes collision and water movement debuffs. This helps centralize all behavior, and allows for easy modification to movement mechanics and addition to new debuffs or buffs such as in-water movement.

- These following properties are available to customize
  * `moveMultiplier`: Movement speed for the object. `0.5F` is the default.
  * `waterResistance`: Movement speed `multiplier` when the object is in water. `1.0F` is the default.
    * Anything `less than 1.0F` slows the object movement down.
    * Anything `greater than 1.0F` speeds the object movement up.
    * `No debuff` is applied if the value is `exactly 1.0F`.

### Player (`Player.cs`)
---
This script controls the entirety of a player GameObject, and is the main driver for the player-controlled character. It extends `Movement.cs` to have a unified movement behavior, and receives all of the Movement class's fields.

\[ROBERT'S STUFF\]
- Player has a reference to their own Inventory Manager (`InventoryManager.cs`) as a field for easy access.
- Player overrides parent (base) `Start()`, calls `base.Start()`, then sets the `currentHealth` and `currentThirst` to `maxHealth` and `maxThirst`, and sets it to the respective visual bars.
- `FixedUpdate()` takes user input and calls its parent's, `Movement`, `MoveDirection` method that takes in a `vector2` of its x and y movement based on user input.

- **Implementation of `HealthBar.cs`**


	- **TakeDamage** - arguments: **int damage** - subtracts from the current health by the **damage** input. This will then call the SetHealth function from `HealthBar.cs` to update the health bar object.

	- **HealthRegen** - arguments: **void** - checks first if currentHealth is lower than maxHealth, if so, updates a time to include deltaTime, this ensures that the health is not regenerated every frame, but at a set time. The next comparison chech if the time is greater than or equal to **ThirstHealthDebuff()** and update the Plauyer's currentHealth and resets the timer.

	- **Update** - arguments: **void** - this is called once per frame. This includes some testing for taking damage and calls **HealthRegen()**. 

- **Implementation of `ThirstBar.cs`**


	- **BecomeThirst** - arguments: **int thirst** - validates input, then will **subtract** from the Player's current thirst by **thirst** input. This will then call the SetThirst function from `ThirstBar.cs` to update the thirst bar object. 

	- **RecoverThirst** - arguments: **int thirst** - validates input, then will **add** to the Player's current thirst with the input **thirst**. This will then call the SetThirst function from `ThirstBar.cs` to update the thirst bar object. 

	- **ThirstHealthDebuff** - arguments: **void** - this will return a float to work with the **HealthRegen** function. Based on currentThirst, this will return a float increasing by 5% for each 25% decrease of the Player's currentThirst. 

	- **Update** - arguments: **void** - this is called once per frame. This includes some testing for taking damage. Calls **BecomeThirst()** after an appropriate key press and **RecoverThirst()** after an appropriate key press. 
		
### Health Bar (`HealthBar.cs`)
---

This sets up the health bar system for the player object. This extends `MonoBehaivor`.
- This features two functions that set integers realating to the Player's health. 
- Respectively, this will then effect the slider object attached to the player. 

(See `Player.cs` for implementation of these scripts)
### Thirst Bar (`Thirstbar.cs`)
---

Similar to the health bar, this will set the thirst bar system for the Player. This extends `MonoBehaivor`.
- This features two functions that set floats relating to the Player's thirst. 
- Respectively, this will then effect a seperate slider object attached to the player.

(See `Player.cs` for implementation of these scripts)
### Camera Motor (`CameraMotor.cs`)
---
The Camera Motor is the main driver for the primary player camera, which extends `Movement.cs` in order to have all the unified movement behavior and properties as any other entity that requires it.

- There is an extra field, `lookAt`, which can be set to any GameObject to tail.
- Additionally, `boundX` and `boundY` define how far the object in focus needs to move before the camera begins to follow along.
- The `Start()` method overrides the `Base` `Start()` method in `Movement.cs`. It still calls the base `Start()` with `Base.Start()`, then overrides the default `blockingMasks` that will halt movement; I.E. the gameObject masks to collide with.
- The Camera Motor also comes equipped with a "Panic" system in case the Camera gets stuck around a sharp turn or tight squeeze in collision objects, that takes two fields:
  * `panicDistance`: The distance the `lookAt` object needs to get away from the camera before disabling collisions.
  * `panicEnd`: Control field to detail the end of the panic (`panicStart` + `2 seconds`). If the panic is enabled, then `panicEnd` will be the time in which collisions will be re-enabled and dictate the end of the panic.

### Item Database (`ItemDatabase.cs`)
---
Item database stores all instances of unique items to be quickly referenced and copied into the player's inventory.

- All Item instances are declared upon `Awake()` to allow for quick retrieval when in-game.
  * Currently implemented via a list; Dictionary<int, Item> will be implemented next sprint.
- GetItem() fetches an item from the database via ID or Name.
- `GameManager` now holds a reference to the ItemDatabase GameObject to quickly reference wherever needed to forego a costly fetch.

### Lerp (`AutoLerp.cs`)
---
This is a simple script to allow for an item's color property to cycle through a given list of colors at a given interval of time.

- It has the following customizable fields:
  * `active`: Defines whether or not to Lerp.
  * `specialColors`: Defines the colors to cycle through; takes Unity `Color` statics.
  * `colorTransitionTime`: The amount of seconds to smoothly transition between colors in `specialColors`.

### Player Inventory (`InventoryManager.cs`)
---
InventoryManager stores all items that the player has in a list, along with keeping track of the weight.

- It contains a reference back to ItemDatabase for quick access.
- `GameManager` now holds a reference to the InventoryManager GameObject to quickly reference wherever needed to forego a costly fetch.

UML DIAGRAM
```
InventoryManager {
public
------
ItemCount(Item item | int id | string name) : int
GiveItem(Item item | int id | string name) : bool
RemoveItem(Item item | int id | string name) : bool
CanCarry(Item item) : bool
}
```
- GiveItem() checks weight against the current haul, and returns true if it was able to add to the player's inventory, and increments current weight based on the item weight.
- RemoveItem() returns true if it found and removed an item from the inventory, and decrements the current weight based on the item weight.
- CanCarry() is a helper function to see if an item's weight is able to be carried based on the current weight being carried.

### Floating Text Manager (`FloatingTextManger.cs`)
---
Floating Text manager is meant to drive forward the floating text.
- Update Method 
	- This method is meant to work as a refresh to the text and make sure that it runs the amount of time needed and doesn't stay longer than needs to be. Calls the method `UpdateFloatingText` in `FloatingText.cs` to make sure this happens correctly.
- GetFloatingText Method
	- This method will check to see if there is currently a text active if not, it will retrieve a text, instantiate it, and send it back to the `Show` method.
- Show Method
	- Show will set all fields of a floatingText object. This includes the actual text (`msg`), `fontSize`, `color`, `position`, `motion`, and `duration`. This will finally call the show method in the `FloatingText.cs` file.


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

### Floating Text (`FloatingText.cs`)
---
This file is meant to hold the very basics for showing, hiding, and updating the text currently on screen. This file also holds all the fields of floatingText.
- Fields:
	- `bool` active.
		- Shows whether a text is currently active or not.
	- `GameObject` go
		- Works to update the text in unity through GameManager
	- `Text` txt
		- This is the actual text that will show up in game.
	- `Vector3` motion
		- This is how we want the text to move in game. This includes the text sliding up, down, left or right.
	- `float` duration
		- How long we want the text to show up on screen.
	- `float` lastShown
		- When the text was last on screen.
- Show Method
	- Will set the `active` field to true, set the `lastShown` field to the time in the engine that is current, and call to set the text to active.
- Hide Method
	- Will set the `active` field to false, and call to set the text as inactive.
- UpdateFloatingText
	- Will check the `active` field first and check if it is inactive, will return if so. Will then make sure that the `lastShown` field is not greater than the wanted duration of the text. Finally will update the motion of the text, or more specifically the current position of the text. 

---