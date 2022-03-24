# User Stories

## Table of Contents
---
1. [Main Menu Format](#1-main-menu-format)
    1. [Start a new save](#11-start-a-new-save)
    2. [Load a previous save](#12-load-a-previous-save)
    3. [Configure key game options](#13-configure-key-game-options)
2. [Controls](#2-controls)
    1. [Movement, forward, back, left and right.](#21-movement-forward-back-left-and-right)
    2. [Interacting with objects/items. Picking up or dropping.](#22-interacting-with-objectsitems-picking-up-or-dropping)
    3. [Combat Controls.](#23-combat-controls)
3. [Gameplay](#3-gameplay)
    1. [In-game world movement](#31-in-game-world-movement)
    2. [Replayability](#32-replayability)
    3. [Story Elements](#33-story-elements)
4. [Difficulty](#4-difficulty)
    1. [Enemies](#41-enemies)
    2. [Difficulty Choices](#42-difficulty-choices)
5. [Progression](#5-progression)
    1. [Story Progression](#51-story-progression)
    2. [Game Progression](#52-game-progression)
6. [Player Choices](#6-player-choices)
    1. [Combat](#61-combat)
    2. [Scavenging](#62-scavenging)
7. [Visuals](#7-visuals)
    1. [NPCs](#71-npcs)
    2. [Environment](#72-environment)
8. [Adaptability](#8-adaptability)
    1. [Game Resolution](#81-game-resolution)
    2. [Playability](#82-playability)
9. [In-Game Menu](#9-in-game-menu)
    1. [Main Game Menu](#91-main-game-menu)
    2. [Inventory Menu/Crafting Menu](#92-inventory-menucrafting-menu)
10. [Time Management](#10-time-management)
    1. [Forced teleport to boss room](#101-forced-teleport-to-boss-room)
    2. [Ramped up events as time runs out](#102-ramped-up-events-as-time-runs-out)
---
---

## 1. Main Menu Format<sup>[\[Back to Top\]](#user-stories)
---
> ### As a player, I want to be able to navigate the main menu when I open the game for the first time with relative ease.

### 1.1 Start a new save<sup>[\[Top\]](#user-stories)

As a player, I want to be able to create a new game with my desired difficulty level so that I can be comfortable playing at my own pace.

**Elaboration**: I want to be able to go into a new game, especially as a first-time player, and be able to declare whether I want a challenge, or if I want to relax if I am more of a casual player, that way I can enjoy the game at my own pace.

**Constraints**: There should be 3 to 5 save files so that users can experiment with different difficulties and no more than 5 to save space both visually in the menu and storage space, and also because realistically someone would not want to finish the game in 50 different saves.

**Effort Estimation**: 2 person-hours.

**Acceptance Test**: Create a save on an “EASY” difficulty, one on a “MEDIUM” difficulty, and one on a “HARD” difficulty, and have my progress save after a tutorial so I can pick and choose later on based on which difficulty I am settling with.

### 1.2 Load a previous save<sup>[\[Top\]](#user-stories)
As a player, I want to be able to load previous saves without losing any data and knowing what each save contains, including unlocks and difficulty, so that I can choose my preferred game run based on how I am feeling, or if a sibling or friend wants to load their individual save.

**Elaboration**: Games are meant to be shared and experienced with others, especially ones that are super short and easy to get into like rogue-likes. The ability to differentiate saves on more than just the custom save name, being able to differentiate with elements such as unlocks, total runs and time played, and difficulty, would help to differentiate between a set of saves, or even share saves and check how someone is progressing.

**Constraints**: None.

**Effort Estimation**: 2 person-hours.

**Acceptance Test**: I am able to tell which save is mine, or which specific “setup” from a save fits my current mood of casual or serious, without looking at the name of the save. I should also be able to recognize any improvement in my own game by seeing stats go up such as time, wins-to-runs ratio, and unlocks.

### 1.3 Configure key game options<sup>[\[Top\]](#user-stories)

As a player, I want to be able to configure my game to my own liking such as volume, input, and any available accessibility options, so that I can enjoy the game at the right setup and configuration, including any accessibility needs like colorblind filters.

**Elaboration**: Audio mixes are not universally accepted. Some users like only music and no sound effects, maybe softer music and louder sound effects, or just overall a quieter volume in case they are listening to music in an external application like YouTube or Spotify. Additionally, I may be colorblind, in need of differentiating enemies from the background in case the two colors happen to directly align with my own colorblind diagnosis. I might also use a different keybind setup other than WASD, such as IJKL, or the arrow keys.

**Constraints**: Simple audio controls: overall, music, and sound effects. Accessibility tools: colorblind filter.

**Effort Estimation**: 8 person-hours.

**Acceptance Test**: I should be able to set my volume easily in game or in the menu based on my own personal preferences or on the situation like listening to a podcast or music in the background, I should also be able to rebind my keys from the default WASD scheme to the arrow keys, IJKL, or any random arbitrary configuration of keys as long as there are no conflicts, and I should be able to set the colorblind filter to my specific colorblind diagnosis if I have one.

---

## 2. Controls<sup>[\[Back to Top\]](#user-stories)
---
> ### As a player, I would like the game to explain controls in detail and how to interact with the game as intended.

### 2.1 Movement, forward, back, left and right.<sup>[\[Top\]](#user-stories)
As a player, I want to know how the movement in the game should be used and implemented so that I can progress through rooms/story.

**Elaboration**: A user should be told distinctly how they should be using controls. Movement is important in a video game, otherwise no progress can be made.

**Constraints**: A player will not be able to walk into every crevice in the game, and there will be constraints in terms of invisible walls, collision, etc..

**Effort Estimation**: 4 person-hours.

**Acceptance Test**: I should be able to successfully move around the map without having the trouble of not knowing how to get around. I should know when I am facing a collision or if the movement is just not working as intended.

### 2.2 Interacting with objects/items. Picking up or dropping.<sup>[\[Top\]](#user-stories)
As a player I want to know how objects are going to be used to influence my experience in the video game because objects have a multitude of uses, or none at all, and knowing those choices is important.

**Elaboration**: In a game where objects can be important to the story, there should always be explicit directions on how items should be used, stored, discarded, etc.

**Constraints**: None.

**Effort Estimation**: 4 person-hours.

**Acceptance Test**: I should be able to know which items can be used where, how, and even when. Well directed interaction with any object in the game would be considered a successful test.

### 2.3 Combat Controls.<sup>[\[Top\]](#user-stories)
As a player, I want to know how fighting other creatures, people, or any other enemies that are put into the game should be done so that combat progress can be made successfully.

**Elaboration**: Combat can typically lead to life or death situations. It would be quite important to know how to keep me, the player, alive in a situation where combat is my main survival tactic.

**Constraints**: None.

**Effort Estimation**: 4 person-hours.

**Acceptance Test**: I should be able to successfully complete combat, whether that means hurting an entity or being hurt by an entity, and know how it is happening.

---

## 3. Gameplay<sup>[\[Back to Top\]](#user-stories)
---
> ### As a player, I would like the gameplay and mechanics to be well-rounded and challenging, yet fair, so that it is not frustrating or boring.

### 3.1 In-game world movement<sup>[\[Top\]](#user-stories)
As a player, I want to know where and how freely I can move across the main areas and other various set locations throughout the game.

**Elaboration**: If the set environment is not clear about where I, the player, can move around to, it is possible to become lost or unsure of how to proceed forward.

**Constraints**: There are set rooms/areas, this is not open world. The player will run into borders, but will match with in-game visuals that can also guide players. 

**Effort Estimation**: 3 person-hours.

**Acceptance Test**: I should be able to see and understand where I, the player, can move about without getting stuck, lost, or breaking the game. Elements such as world borders and in-game visuals should provide some aid as to how to proceed forward with the game.

### 3.2 Replayability<sup>[\[Top\]](#user-stories)
As the player, I want enough in-game diversity that I would be able to play through the game again and experience a new and/or different run through.

**Elaboration**: Difference in difficulty, multiple endings, changes in enemy/item spawn rates would all provide new and unique run throughs if I played through the game again.

**Constraints**: None.

**Effort Estimation**: 6 person-hours.

**Acceptance Test**: After a successful runthrough of the game, I should be able to play through once again with difference in difficulty, item drops, enemy spawns, etc. 

### 3.3 Story Elements<sup>[\[Top\]](#user-stories)
As a player, I want to have some interest in the story of the game. Some basic story design elements should take place in order to keep me, the player, engaged to the game.

**Elaboration**: As a survival rogue, the game should have some sort of interesting storyline that should include some danger to push that survival feeling. 

**Constraints**: None.

**Effort Estimation**: 3 person-hours.

**Acceptance Test**: The start, throughout, and the ending of the story should be thoughtful and interesting as to fully keep me, the player, engaged with the game. Whether it is satisfying or not, I, the player, should be left with some sort of feeling of completion after having finished the initial run through of the game.

---

## 4. Difficulty<sup>[\[Back to Top\]](#user-stories)
---
> ### As a player, I would like the game to present some challenge, while not being overly difficult. 

### 4.1 Enemies<sup>[\[Top\]](#user-stories)
As a player, I want to have interaction with enemy npc’s. Enemies should inflict damage during encounters for danger elements.

**Elaboration** Since the game is survival centered, a health system should be implemented along with death that can be caused by enemies.

**Constraints** Natural Health regen may or may not be implemented, meaning I as the player need some way to regain lost health.

**Effort Estimation** 2 person-hours.

**Acceptance Test** In enemy encounters, I should see loss of health and regain of health in appropriate context. 

### 4.2 Difficulty choices<sup>[\[Top\]](#user-stories)
In the game menu, I want to be able to choose different difficulties before starting the game or for a new iteration of the game.

**Elaboration** Game difficulty settings should have direct effects on the game. Whether it be for item drops or aggression/damage from enemies. I, as the player, should notice some difference between difficulties.

**Constraints** None.

**Effort Estimation** 1 person-hour.

**Acceptance Test** Different difficulties on different run throughs of the game should yield different results in enemy damage and/or useful items discovered in the game.

---

## 5. Progression<sup>[\[Back to Top\]](#user-stories)
---
> ### As a player, I would like the game to allow me to know when I’m making progress through story or any kind of quest in the game.

### 5.1 Story Progression<sup>[\[Top\]](#user-stories)
As the player, knowing when I’m successfully progressing through the story is extremely important.

**Elaboration** Stories for games can get complicated, really in the ways that the creator of the game wants the user to progress. This can include finding items, finding npcs, or going to certain areas that will help the story.

**Constraints** None.

**Effort Estimation** 4 person-hours.

**Acceptance Test** Would a new player know how to get through the story easily without having to struggle their way through every part of the game.

### 5.2 Game Progression<sup>[\[Top\]](#user-stories)
As a player, progressing through the game itself is important in ways of knowing how to solve the obstacles that I’m finding myself in.

**Elaboration** Game progression is different usually because these are things that can be randomly found in the game without being needed to progress through the story. This can be fighting off random enemies, solving extra puzzles, etc.

**Constraints** Specify what is game progression and what is story progression. 

**Effort Estimation** 3 person-hours.

**Acceptance Test** Can a player successfully go through the obstacles that they find themselves in throughout the game, if so it is a success. 

---

## 6. Player Choices<sup>[\[Back to Top\]](#user-stories)
---
> ### As a player, I would like to be able to steer the story in my own direction, while also being able to have freedom of choice when engaging in combat and scavenging, so that I can learn from previous mistakes and build strategies to have a more successful run on my own merit.

### 6.1 Combat<sup>[\[Top\]](#user-stories)
As a player, I would like to engage in combat with my own strategies rather than having it pre-written for myself, so that I can utilize my own gear however I see fit.

**Elaboration** This will allow for better pre-planning, and higher replayability, as I can learn from my own mistakes and shortcomings, along with what went well for my next run.

**Constraints** Whatever I have in my inventory.

**Effort Estimation** 4 person-hours.

**Acceptance Test** I am able to fight in multiple different ways regardless of what I have in my inventory, even if I have the same items three or more runs in a row.

### 6.2 Scavenging<sup>[\[Top\]](#user-stories)
As a player, I would like to have the liberty to choose what I would like to pick up from the environment and what I will drop if I run out of room, rather than have pre-assigned items that are immutable, so that I can create the build that I want with the resources I run into.

**Elaboration** This will allow for heavy replayability as each run will have different items, and a player can learn what are good synergies to have and what items are just dead weight if they do not have something that will synergise with it.

**Constraints** None.

**Effort Estimation** 4 person-hours.

**Acceptance Test** I am able to pick up and drop items at will, as many times as I would like, without having any item forced into my inventory.

---

## 7. Visuals<sup>[\[Back to Top\]](#user-stories)
---
> ### As a player, simple yet clear visuals should be implemented and relate to the actual gameplay.  

### 7.1 NPCs<sup>[\[Top\]](#user-stories)
As a player, I would like to be able to see, to some extent, a clear picture of enemies and other npc’s. 

**Elaboration** The NPC’s design should correlate to some degree with the story and gameplay. I, as the player, would like to avoid confusion of visuals and be able to visually understand what is happening on screen. 

**Constraints** Visuals are not a primary focus, therefore, the in-game look will be very simplistic, either pixel or atari style art.

**Effort Estimation** 1 person-hours.

**Acceptance Test** The npc’s are clearly present on the screen during interactions. 

### 7.2 Environment<sup>[\[Top\]](#user-stories)
As a player, I would like to see some environmental visuals that correspond with the game and story. 

**Elaboration** Certain areas in the game should be represented through visuals. As a player, if I am in a forest, I would like to see trees and such. Eye-candy is preferred, but not a major concern.

**Constraints** Similar to npc’s, visuals will be simplistic within time constraints.

**Effort Estimation** 1 person-hour.

**Acceptance Test** Moving through areas, the visuals should shift accordingly to avoid confusion and loss of gameplay quality. 

---

## 8. Adaptability<sup>[\[Back to Top\]](#user-stories)
---
> ### As a player, the game should be relatively easy to run and use. 

### 8.1 Game resolution<sup>[\[Top\]](#user-stories)
As a player, I would like to avoid conflicting resolutions if the game was played on different screens. 

**Elaboration** With the simplistic visuals, there may be a fixed resolution, As a player, no matter the screen using, the game should still be playable.

**Constraints** None.

**Effort Estimation** 1 person-hours.

**Acceptance Test** Launching the game on different screens should yield the same or adapted resolution. 

### 8.2 Playability<sup>[\[Top\]](#user-stories)
As a player, I should be able to load the game in with minimum requirements.

**Elaboration** The game should be able to launch without any preliminary downloads such as unity or external files.

**Constraints** String 

**Effort Estimation** 2 person-hours.

**Acceptance Test** I should be able to launch the game after successful download, and the game should run correctly.

---

## 9. In-Game Menu<sup>[\[Back to Top\]](#user-stories)
---
> ### As a player, I would like a simple in-game menu with clear save, exit, and options so that I do not have to fumble and scour menus in order to perform the action I wish.

### 9.1 Main Game Menu<sup>[\[Top\]](#user-stories)
I as the user would like an easy navigable main menu and see my options.

**Elaboration** Some game menus can be made overcomplicated and hard to use. A menu that easily lets me know where to click and what the options will do. 

**Constraints** Simple menu that would not cause confusion.

**Effort Estimation** 3 person-hours.

**Acceptance Test** If I as a player can easily navigate the menu, that would be a successful test..

### 9.2 Inventory Menu/Crafting Menu<sup>[\[Top\]](#user-stories)
As the player, the inventory of my character is important and how I get to interact with that menu is just as important as anything else.

**Elaboration** Being able to use my items easily and craft with them is important. I would not like to sit around in a menu for multiple minutes trying to figure out how I should be able to use the items in my inventory for my benefit.

**Constraints** Creating a fast and easy inventory management/use that would not make the player have to check every nook and cranny of the menu to do what they wish with their items.

**Effort Estimation** 4 person-hours.

**Acceptance Test** If I as the player can do what is intended with the items I have available, that would be considered acceptable.

---

## 10. Time Management<sup>[\[Back to Top\]](#user-stories)
---
> ### As a player, I would like to feel a sense of urgency in order to continue to progress through the story instead of feeling like I have all the time in the world to go about it, so I can learn to face enemies and collect resources under pressure.

### 10.1 Forced teleport to boss room<sup>[\[Top\]](#user-stories)
As a player, I would like to be teleported to the boss if I do not reach the boss room in time so that I have motivation to min-max and manage my time efficiently.

**Elaboration** It will bring more of a challenge to have a time limit imposed upon the player, allowing for more dynamic use of one’s time, and also learning from previous shortcomings of not utilizing time efficiently.

**Constraints** 10 minutes at most on easy mode down to 5 in hard.

**Effort Estimation** 1 person-hour.

**Acceptance Test** I should be teleported to the boss room as soon as the timer runs out.

### 10.2 Ramped up events as time runs out<sup>[\[Top\]](#user-stories)
To encourage early scavenging and playing through the game faster, the game clock should enhance the possibility of disasters to occur, but also more higher-tier items to appear, so that I can also take into consideration risk-reward.

**Elaboration** This would add an extra layer of difficulty that can enhance how I approach survival mechanisms.

**Constraints** None.

**Effort Estimation** 4 person-hours.

**Acceptance Test** I should be able to find higher-tier and more useful items more often later into the current floor’s timer, and also experience more frequent disasters.
