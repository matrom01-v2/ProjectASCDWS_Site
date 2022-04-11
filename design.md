# Project Design

## Brief Key Architectural Drivers
> ### The Why

For figuring out what we needed for our architecture, we first needed to know how this game was going to be played, accessed and used. With this in mind, our game is a singleplayer game with no real need to access any outside information other than your saves and the game data. This would allow us to use a more secluded architecture that could be downloaded and work independently from any other systems.

We would need the game to be able to respond to updates in the system. This includes entering new areas, inventory systems, saved data, NPC interaction, and the combat system. Our code is currently based on classes. This means that every  component is coded separately but they are also able to easily interact with each other. An example of this is our collidable class and NPCs/Player classes. These classes are able to interact to centralize reusable code.

---

## Blackboard Architecture
> ### The How

![ARCHITECTURE DRAWING](https://user-images.githubusercontent.com/90274287/161161066-57d9bf90-0e91-4b86-8368-7f872e60ff9b.png)

{Design Explanatory Text}

{Response to feedback given here: [\[link\]](https://nmsu.instructure.com/courses/1434741/assignments/11849929/submissions/3728078)}
<details>
<summary>
<<< Read Toupes' Feedback (<strong>TAP/CLICK ME TO EXPAND AND READ</strong>) >>>
</summary>
<p>

working on combat system
inventory subsystem
survival game, so what items are carried and left behind are core decisions
focus on survival aspect – outdoor map with obstacles

> need a good model of survival components – health, regeneration rate, hunger, thirst – probably a major piece of the design and part of the architecture

single player game, so not server/client

working all locally

repository – database vs blackboard

database that's run locally – issue is that read and write requests, concerns about latency caused by hard drive writes

> so there's probably settings for this; most likely some part of the database that's in regular use should be loaded into memory, but it would regularly need to be written to the backing store. 

blackboard approach – use an in-memory object

> really make sure that you look at the Singleton Design Pattern. Be really careful about having a global for tracking the blackboard, but you can essentially pass a reference to a single, canonical blackboard object. Note too that you'll need to ensure that access to the blackboard is synchronized appropriately. You'll probably find that having a set of known constant keys that get mapped to values in the blackboard. (So objects like HashMap / HashTable / Map / etc.)

https://refactoring.guru/design-patterns/singleton
Z Toups , Apr 1 at 1:11pm
</p>
</details>


---

## Singleton Blackboard
> ### Meet: The GameManager

---

## Game Objects and Connections

---

## Static Classes

---