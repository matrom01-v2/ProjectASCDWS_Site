# Requirements Specification for Feast for a Crow

## 1. Introduction

### 1.1 Purpose of Product

Feast for Crows (working title) is a top-down 2D survival game meant to challenge the player with its rogue-like elements of fast, ever-changing and replayable gameplay. The core elements of the game will include Atari style graphics, reminiscent of games such as The Binding of Isaac or Faith. Players can and will encounter hostile situations including wildlife, sustenance, enemy NPCs, and *something else*. Among the wildlife, there are two mini bosses and one final boss to add to the overall difficulty and stakes. This game’s primary purpose should be to provide a challenge of wit over brawn, forcing the player to utilize resources efficiently and plan out what to keep and what to discard.

### 1.2 Scope of Product

The scope of this product is a simple rogue-like game to be developed within 6 weeks, with a simple inventory, movement, and combat system. The story and combat will be played out within text boxes with a varying amount of on-screen user choices, and will have simple 3-piece text structures to avoid repetition in text-based actions.

### 1.3 Acronyms, Abbreviations, Definitions

**Rogue-Like**: Roguelike (or rogue-like) is a subgenre of role-playing video games characterized by a dungeon crawl through procedurally generated levels, turn-based gameplay, grid-based movement, and permanent death of the player character. Most roguelikes are based on a high fantasy narrative, reflecting their influence from tabletop role playing games such as Dungeons & Dragons.
[Source](https://en.wikipedia.org/wiki/Roguelike)
 
**Text-Based**: A text game or text-based game is an electronic game that uses a text-based user interface, that is, the user interface employs a set of encodable characters, such as ASCII, instead of bitmap or vector graphics.
[Source](https://en.wikipedia.org/wiki/Text-based_game)
 
### 1.4 References

The following are games that inspired the product that we are producing, including elements like graphics, text-driven story, and rogue-like combat and navigation.

[The Binding of Isaac, about the game](https://bindingofisaacrebirth.fandom.com/wiki/Binding_of_Isaac:_Rebirth_Wiki)

[Noita, the game](https://noitagame.com/)

[To the Moon, the game](https://freebirdgames.com/games/to-the-moon/) 

## 2. General Description of Product

### 2.1 Context of Product

Our product will be a class project. This is an assignment that will run throughout the course of 8 weeks total, left with 5 weeks at current time. 

### 2.2 Domain Model with Description

!MODEL!

The model shown above will allow for easy saving of multiple game states such as player's inventory, position in the scene they are located within, and the position and state of both the player and the enemies around them.

Additionally, it allows for flexibility when it comes to adding more items or collectable types, as they are all funneled into the game's scene to save its status. The GameState will also allow for different story-heavy elements like what bosses are unlocked, or what experiences they have already encountered, in order to change the verbage of the story or responses as the game progresses. Flexibility will also assist in adding more scenes and levels, and an infinite amount of enemies, as the framework for them will be present in areas such as movement and the text menus leading to fighting sequences.

### 2.3 Product Functions (general)

This is a roguelike game that will follow a text based story. This game should have replayability that would allow the player to learn from their mistakes and go back to successfully go through the story however many times they wish or need. Some important mechanics about this game would follow inventory management, choices, and more. 

### 2.4 User Characteristics and Expectations

The user, or player in this case, will be able to control what items they wish to use, what they want to fight or engage with, where they wish to move, and how they wish to progress the story at whatever pace. The user will also be able to manage their items and keep track of where they’ve been.

### 2.5 Constraints

We are limited to the tools that unity has and to the code we can write in C#. Though we are allowed to code quite a bit into the game, we are also constricted to time. We can’t really build a Skyrim like game within 5 weeks even with weekends included. We are also limited by our own ideas and abilities.

### 2.6 Assumptions and Dependencies

Our game relies on Unity in general. Anything that Unity supports, our game can support as well. We cannot have unsupported systems in the game that could be considered “mods” as not everyone will have them and won’t be able to run the game properly. Due to the game being a 2D game there are no real system constraints or assumptions, any modern machine should be able to handle running this game.

## 3. Functional Requirements
[**Go to Functional Requirements**](https://matrom01-v2.github.io/ProjectASCDWS_Site/userstories)

## 4. System and Non-functional Requirements

### 4.1 External Interface Requirements (User,Hardware,Software,Communications)

This game is a Unity-driven product. Unity provides all necessary packages and scripts needed to run after the build folder is downloaded. The user only needs to download the ZIP file with the game’s executable and libraries inside.
 
**NF.4.1.1** - Workable PC or MAC device

**NF.4.1.2** - Game-build folder download
 
### 4.2 Performance Requirements

The product is a 2-Dimensional game, performance requirements are very light. The following specifications are based off of a much heavier 2D game, The Binding of Isaac. 

**NF.4.2.1** - 1GB RAM

**NF.4.2.2** - Minimum OS: Windows XP, Vista 7

**NF.4.2.3** - Minimum Video Card: DirectX9 compatible or higher

### 4.3 Design Constraints

Designs are minimal and simple. Sprites or very rough artwork will be used for NPC’s, the player, and other visuals.

**NF.4.3.1** - Simplistic sprites, used from external sources

**NF.4.3.2** - Background art and visuals. 

**NF.4.3.3** - 2D artwork and sprites, 3D models will not work.

## 4.4 Quality Requirements

The game should offer a decent story with simplistic visuals. Since the visuals are simple, the story and gameplay should carry users through the game. In order to promote replayability, a difficulty setting would be a great addition.

**NF.4.4.1** - Story elements, engaging storytelling to keep the user playing the game.

**NF.4.4.2** - Combat interactions,  health and survival choices that can cause death

**NF.4.4.3** - Text-based interactions, all interactions and story telling will be done through text boxes.

### 4.5 Other Requirements

**NF.4.5.1** - Time Constraint, because of allotted time, some game elements, the less important ones may be dropped.

## 5. Appendices

!!!