# User Stories

## Table of Contents
---
1. [Main Menu Format](#1.%20Main%20Menu%20Format)
2. [Controls](#2.%20Controls)
3. [TITLE (probably gameplay)](#)

---
---

## 1. Main Menu Format
---
> ### As a player, I want to be able to navigate the main menu when I open the game for the first time with relative ease.

### 1.1 Start a new save

As a player, I want to be able to create a new game with my desired difficulty level so that I can be comfortable playing at my own pace.

**Elaboration**: I want to be able to go into a new game, especially as a first-time player, and be able to declare whether I want a challenge, or if I want to relax if I am more of a casual player, that way I can enjoy the game at my own pace.

**Constraints**: There should be 3 to 5 save files so that users can experiment with different difficulties and no more than 5 to save space both visually in the menu and storage space, and also because realistically someone would not want to finish the game in 50 different saves.

**Effort Estimation**: # person-hours: 2

**Acceptance Test**: Create a save on an “EASY” difficulty, one on a “MEDIUM” difficulty, and one on a “HARD” difficulty, and have my progress save after a tutorial so I can pick and choose later on based on which difficulty I am settling with.

### 1.2 Load a previous save
As a player, I want to be able to load previous saves without losing any data and knowing what each save contains, including unlocks and difficulty, so that I can choose my preferred game run based on how I am feeling, or if a sibling or friend wants to load their individual save.

Elaboration: Games are meant to be shared and experienced with others, especially ones that are super short and easy to get into like rogue-likes. The ability to differentiate saves on more than just the custom save name, being able to differentiate with elements such as unlocks, total runs and time played, and difficulty, would help to differentiate between a set of saves, or even share saves and check how someone is progressing.

Constraints: None.

Effort Estimation: # person-hours: 2

Acceptance Test: I am able to tell which save is mine, or which specific “setup” from a save fits my current mood of casual or serious, without looking at the name of the save. I should also be able to recognize any improvement in my own game by seeing stats go up such as time, wins-to-runs ratio, and unlocks.

### 1.3 Configure key game options

As a player, I want to be able to configure my game to my own liking such as volume, input, and any available accessibility options, so that I can enjoy the game at the right setup and configuration, including any accessibility needs like colorblind filters.

**Elaboration**: Audio mixes are not universally accepted. Some users like only music and no sound effects, maybe softer music and louder sound effects, or just overall a quieter volume in case they are listening to music in an external application like YouTube or Spotify. Additionally, I may be colorblind, in need of differentiating enemies from the background in case the two colors happen to directly align with my own colorblind diagnosis. I might also use a different keybind setup other than WASD, such as IJKL, or the arrow keys.

**Constraints**: Simple audio controls: overall, music, and sound effects. Accessibility tools: colorblind filter.

**Effort Estimation**: # person-hours: 8

**Acceptance Test**: I should be able to set my volume easily in game or in the menu based on my own personal preferences or on the situation like listening to a podcast or music in the background, I should also be able to rebind my keys from the default WASD scheme to the arrow keys, IJKL, or any random arbitrary configuration of keys as long as there are no conflicts, and I should be able to set the colorblind filter to my specific colorblind diagnosis if I have one.

---

## 2. Controls
---
> ### As a player, I would like the game to explain controls in detail and how to interact with the game as intended.

### 2.1 Movement, forward, back, left and right.
As a player, I want to know how the movement in the game should be used and implemented so that I can progress through rooms/story.

**Elaboration**: A user should be told distinctly how they should be using controls. Movement is important in a video game, otherwise no progress can be made.

**Constraints**: A player will not be able to walk into every crevice in the game, and there will be constraints in terms of invisible walls, collision, etc..

**Effort Estimation**: # person-hours: 4

**Acceptance Test**: I should be able to successfully move around the map without having the trouble of not knowing how to get around. I should know when I am facing a collision or if the movement is just not working as intended.

### 2.2 Interacting with objects/items. Picking up or dropping.
As a player I want to know how objects are going to be used to influence my experience in the video game because objects have a multitude of uses, or none at all, and knowing those choices is important.

**Elaboration**: In a game where objects can be important to the story, there should always be explicit directions on how items should be used, stored, discarded, etc.

**Constraints**: None.

**Effort Estimation**: # person-hours: 4

**Acceptance Test**: I should be able to know which items can be used where, how, and even when. Well directed interaction with any object in the game would be considered a successful test.

### 2.3 Combat Controls.
As a player, I want to know how fighting other creatures, people, or any other enemies that are put into the game should be done so that combat progress can be made successfully.

**Elaboration**: Combat can typically lead to life or death situations. It would be quite important to know how to keep me, the player, alive in a situation where combat is my main survival tactic.

**Constraints**: None.

**Effort Estimation**: # person-hours: 4

**Acceptance Test**: I should be able to successfully complete combat, whether that means hurting an entity or being hurt by an entity, and know how it is happening.

---

## 3. TITLE