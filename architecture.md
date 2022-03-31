# Project Architecture

## Key Architectural Drivers

For figuring out what we needed for our architecture, we first needed to know how this game was going to be played, accessed and used. With this in mind, our game is a singleplayer game with no real need to access any outside information other than your saves and the game data. This would allow us to use a more secluded architecture that could be downloaded and work independently from any other systems.

We would need the game to be able to respond to updates in the system. This includes entering new areas, inventory systems, saved data, NPC interaction, and the combat system. Our code is currently based on classes. This means that every  component is coded separately but they are also able to easily interact with each other. An example of this is our collidable class and NPCs/Player classes. These classes are able to interact to centralize reusable code.

---

## Blackboard Architecture

### This architecture was chosen over a traditional database system for the following key reasons:

* Write is handled by the Unity Engine in an efficient manner, not writing to the hard drive until significant progress is made.

* Write to the program memory (heap) running the game, and only save to the hard drive with significant progress or on game-close.

* Leads to less stuttering, and does not rely on hard drive read speeds, as reading from and writing to one would bottleneck if the user has slow HDD speeds as the game would have to wait for a response.

### Traditional's Drawbacks:

* Read/Write requests as the game is played.

* Heavy computation and repeatedly writing to a static hard drive running the database instance is slow and bad for HDD health.

* Can be a poor user experience despite being a more common-sense approach to saving user data, even if an item pickup triggers a write.

---

## Architecture Design

![ARCHITECTURE DRAWING](https://user-images.githubusercontent.com/90274287/161160857-b4a36645-af76-4bf8-a40b-ef7a79ac2134.svg)


---

## Conclusion

> ### Repository Style : Blackboard

### Possible Issues:

* Things can easily begin to stack on itself and make it hard to find specific data or objects that we are looking for within our game. Clutter builds easily.

### Risks

* The risk we mostly follow would be user error. Or data corruption. If the user does something that is not meant to be done, such as quitting during a save, that can cause data to get messed up.

* Risks are something we might see more of when or if we do game testing with people outside of the team. They might be able to break something that wasn’t intended to be broken and can help us fix those risks.
