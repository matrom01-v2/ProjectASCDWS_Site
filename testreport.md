# Test Report for Feast for a Crow

## 1. Component Testing

> ### Universal Movement
---
To test the functionality of universal movement (Player, Camera, NPC):
- Player:
    * The ability to move the player around the scene and have the player collide and stop moving with the level borders and any collidable object.
    * Player movement stutters and slows upon entering water.
- NPC:
    * The ability to move around the scene and collide with level borders and any collidable object.
    * NPC movement stutters and slows upon entering water if they do not have 100% water movement resistance.
- Camera:
    * The ability to follow its focus target.
    * Collides with level borders.
    * Panics and removes collisions if its target gets too far away.

These three extensions to Movement inherit the base movement, and the only difference between the three is the camera's "panic" mode.

> ### Collectable
---
To test the functionality of Collectables (any interactable object that can give items), we can test this by having the Player interact with any Collectable object in the scene and receive the Items contained within if the incoming weight does not overburden the Player's inventory.

For example, the current extension to Collectable is: Chest.
- The player will interact with multiple different Chest objects with different items contained within, and receive the contents of the Collectable if the incoming weight does not overburden the Player's inventory.

Another extension is Pick-Up:
- The player will interact with a Pick-Up item on the ground, and if the incoming item's weight does not overburden the Player, it will be picked up, logged to the Debug Console, and the gameObject will be destroyed, removing it from the scene.

> ### Chest
---
To test the lock functionality of the Chest, the Player can wield different kinds of keys, but only the correct KEY_ID will be accepted as a key to unlock the chest. If successful, the Chest will unlock and give the player the items it contains if the Player can hold the extra incoming weight.

> ### Inventory
---
To test the functionality of Inventory, we can combine this with tests with Collectable, as any Item that is picked up or collected by the player will be logged to the Debug console (later, displayed in the In-Game Menu), along with showing the current weight being carried by the Player.

If an **incoming item's weight** (I.E. any Collectable) **plus** the **current weight being carried** is not greater than the **max weight**, then the Item will be added to the Inventory and add the **incoming item's weight** to the **current weight** and display properly in the Debug Log; else, it will display that the Player is carrying too much.

If a Player uses a Key item, it will be removed from the Player's inventory, and the result will be logged to the Debug Log along with the new weight, which should update with the **current weight minus** the **key's weight**.

> ### In-Game Menu UI
---
To test the functionality of the in-game menu we have to make sure that the stats for the player would automatically update when something was changed. Current implemented stats on the menu are:
- Health
- Thirst or "thorst"
- Health Regen Rate
- Ability to change skins

We would change these stats by making the player take damage, get thirsty, and regen rate would be effected by thirst. Once the player has taken a change to their stats, we had to make sure that there was change applied to the menu, which was successful. We would see an update in text displaying the current Health/Thirst/Regen Rate. Same goes for skin changes, the skin would successfully change on the menu and in game.

> ### Save/Load States
---
For save or load states, we wanted to make sure that the player can successfully save and load their data into the game. For this, we made sure to allow the player to take damage, change their skin, or any other stat change. After any of these stat changes, the player would have to press the save button which would then call the save state method. Then the player would be able to quit the game and load back in which would automatically call the load state method and bring back their previous stats and selected skin.

> ### Health Bar and Regeneration
---
To test the functionality of the health bar taking damage, a simple user input was used to deal damage to the player. If the system works properly, the health bar object of the player should visually decrease along with any numbers accociated with player health.The health regeneration system is tested by user input that deals damage to the player object. If the system works properly, then the health bar slider should increase as do the corresponding numbers accociated with the player's health. This works in conjunction with a **thirst bar** system that will be explained below.  

> ### Thirst Bar
---
To test the functionality of the thirst bar, a simple user input was used to reduce the thirst bar slider object. If implemented correctly, the thirst bar slider will visually decrease along with any accociated numbers to the player object. This works in conjunction with the **health regeneration** system. By reduced thirst stats, the **natural health regeneration rate** of the Player object should be also be **reduced**. This means that the lower the thirst bar, the slower the health will regenerate. Both the health regeneration and thirst systems interact and rely on each other.

> ### Animations
---
Functionality of animations in the game are represented visually in game. Clear movement of sprites and fluid objects should be visible to the user under the right conditions. 
- **Chests** are one example of animation. A chest visually opens if the user interacts with an openable chest. 
- **Dynamic player movement**

> ### Visuals
---
In-game visuals are clear and responsive. Testing for visuals is as simple as making sure all objects and scenes are visable to the user. The gameplay revolves entirely around the visuals. All objects should make sense and have clear representation of what they are in terms of gameplay. In terms of testing, any and all objects used are visually reperesented on the map or scence, including some interactability with the user such as **chests** or **NPC's**.

## 2. System Testing
A series of steps was used to test the system. Initial testing was done on each newly added component, this is refered to as **unit testing**. For every newly added function of the game, it's functionality was tested after implemented into the game. For example, upon the implementation of the UI inventory system, we tested functionality i.e. how to activate the menu, close the menu, proper display overlay in game etc. As components were added and tested for functionality, the next step was to view their interaction with other in-game compontents. This was our **integration testing** phase; seeing how new components or systems work together. Keeping with the UI example, the UI can now accurately utalize and display the user's player statistics: health, thirst, items, and so on. The final step in our testing comes to our **acceptance tests**, whether or not the implementation of systems align with the **User stories** forged for the system.




## 3. Acceptance Testing

> ### 1. Main Menu Format

---
- Current State: ***not implemented***

- Once implemented, we excpect save states of the game to be created and accessed via a main menu on either the title screen or in game. Loading previous saves are expected to be successfully loaded in during testing. At the moment, the main menu stands as not fully implemented, however, we excpect that it will be functional with each component tested before fully integrated.

> ### 2. Controls

--- 
- Current State: ***implemented***

- Through the play test function of Unity, player movement has been tested and yielded successful inegration. The camera functionality follows the player as intended with workable collidable objects the player cannot pass through. Some areas have an intended effect on the player's movement speed. Collisions and collidable objects are clear in via visuals in game. NPC's are also unable to pass through collidable objects. The movement and control system is **completely implemented**.

> ### 3.  Gameplay

--- 
- Current state: ***in development***

- As of now, one aspect of gameplay has been implemented. Gameplay continues to build as more systems and units are implemented. Through all of these new implementations and testing of each new addition, the gameplay itself is cotinuously being tested. Currently, clear movement, world borders, and visual guides have been tested and accepted as **implemented**. Final touches such as story elements have **not yet been implemented**.

> 4. ### Difficulty

---
- Current state: ***in development***

- Enemy NPC's are currently active, but do not yet damage the player. Difficulty choices have not yet been implemented, therefore we cannot say the difficulty system is functional. We expect that once implemented, enemy NPCs will take priority and therefore offer some level of difficulty to keep the user engaged with the combat system. Tests wil be run to make sure player and NPC interaction is not too difficult and not too easy.

> ### 5. Progression

---
- Current state: ***not implemented***

- Game progression relies heavily on story progression and is therefore up in the air in terms of how the game will proceed forward for users. We expect some sort of system that clearly shows progression for the users in game, whether that be defeating all enemies, collect all items, etc. is undecided at the moment. In testing, if the user is able to go through obstacles they find themselves in throughout the game, it will be accepted.

> ### 5. Player Choices

--- 
- Current state: ***in development***

- The combat system, while not yet implemented fully, has most of the major components needed such as health and enemy NPC's. The health abr system and thirst systems have been successfully tested and integrated in the game. Scavenging is also currently in development as the user can successfully pick up items and loot chests. We expect that after testing, players can use objects found or looted and can use such items in conjunction with the other systems such as health or combat. 

> ### 6. Visuals

--- 
- Current state: ***implemented***

- As described in the user stories, current required game visuals are **completely implemented** and tested via the Unity gameplay test features. Moving through areas on screen is accessable and clear. Backgrounds, objects, scenery, NPCs clearly appear how they need to as to avoid confusion for the user. Some additional eye-candy such as trees, lakes, and ponds are also implemented.

> ### 7. Environment

---
- Current state: ***implemented***

- As described in the user stories, current required game environment and visuals correspond with initial intention. Nature like visuals and sprites have been added and tested to make sure the user is able to understand the intended scenery. Visuals shift with the user as they move the player to different areas on the map. These were tested using the Unity play test features and can be considered as **completely implemented**.

> ### 8. In-Game menu

--- 
- Current state: ***implemented***

- The in game menus are currently **implemented**. Menus will have been tested via the Unity play test features as to avoid bugs or damage to other systems/system interactions. The user can pause the game, load save files, see inventory with in game stats. Users can now open an in-game menu with their statistics displayed: health, thirst, and health regen rate. Users can also change their game skin and their decision saved and loaded in successfully. All testing was done with the Unity play testing features. 
