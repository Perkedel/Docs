# s&Cardiophilia Game Design Doc

## Overview

s&cardiophilia is a story focused idle game. It's a unique take of Idle genre where you collect currencies, by waiting a tick, which for this game is a heartbeat, instead of a click something or auto attacking monsters.

### Details

- Title (working): s&cardiophilia
- Genre: Idle ~~Clicker~~
- Target: **PC**. because s&box currently is only for Windows (Proton Wine compatible), tho this may change as Facepunch (being the dev for s&box) added more targets.
- Target Audience: Cardiophilia Fetish, Lazy Cozy, Idle enjoyers

## Mechanics

### Base

s&Cardiophilia is a game about heartbeat fetish. In this game, you collect girls (and cute men later). and these characters have hearts. Each beating heart grants you a Cookie Click, called **Steth Coin**. it can be multiplied through upgrades

- Idle Cookie Clicking
- Get Cookie only possible through each heart systole. You can connect your own pulse monitor to contribute (max 210 BPM).
- each Character can do avtivities that affect heart rate. Make it faster and gain more Steth Coins per minute.

### Characters

Each character not only have unique looks and gender, also have various kinds of hearr conditions. From normal, down to insanely quirky.

### Cookie Clickings

This game only has cookie obtaining by heartbeat. There are rules to how Clicks are considered

- Lub = 1 Click ➡️ 1 (× Multipliers you had) Steth Coin rewarded
- PVC and various kinds of Arythmias. Only first Lub are considered, rest messups (such as 3rd beat e.g.) are ignored until this cycle of begujruk has finished and then next phase. Therefore having Arrythmia and skips can be considered debuff or Blight as in botanical terms. A correct medicine can be used to ameliorate this.
- Tachycardia and Bradicardia. As long the heart still beats considerably Sinus in conclusion, you still have steady flow of Cookie Clicks, Faster and slower respectively. But be mindful of other Fatality caveat chances.
- Fatality. Some heart condition & effects may cause Fatal Consequences, such as Cardiac Arrest, Fibrilations, etc. Interact with the Character that suffered this Consequences & start CPR. Due to its complexity and potential interest debuff this part may cause, we decided to simplify it with just an item `Auto CPR Kit` which costs Steth Coins. A manual feature will be added later, as we understand some Cardiophilia Rabbithole Dwellers are also into CPR fetish as well.

### CPR

Currently, the Heart Fatality Recovery system is simply commence by using item `Auto CPR Kit`. As mentioned before, for those who are into CPR fetish, the CPR minigame provides experience of doing heart recovery, but obviously is **not meant to be compliant with actual CPR training**.

- Start by clicking the Character that suffered Fatality, then click `Start CPR Manually`.
- You must provide breath. Click mouth to blow your breath in. Ensure at certain interval to repeat this.
- Maintain beating the heart manually. Click chest in rhythm and make sure the blood could resume for their brain.
- Keep repeating this until their brain restarts and who knows able to connect back to heart and beats it/those again followed by rest of the recoveries.
- Sometimes, you may also have to clear the heartbeats, such as in Fibrilations (Squirming beat). Use Defibrillator to clear the heartbeats.

We still advise to use `Auto CPR Kit` rigs instead, since Manual CPR is very complicated & time consuming. In case that you do not have enough Steth Coins (e.g. have equals to or less than listed price), DNB will instead pay you on the house and no Steth Coins to be deducted. **No limit**.

### Story Mode

s&cardiophilia being story focused, has quests gamers can follow through.

You have a bedroom which has a bed. Interact with this for Story Quest menu. each story are presented as an animated presentation cutscene with some interactivities.

Every Character that appeared in the Scene, always counts for Cookie Clicking, unlocked, NPC, or neither.

Unfortunately, due to limitation and GameObject tree policy, Characters that do not appear on the tree of loaded Scene won't count, i.e. Heart Organ GameObject forbidden to carry to Always Load (System Scene) during story as it may cause lag. Simply finish or suspend and return to Main Menu to resume many cookie clickings.

### Special events

In each patch, s&Cardiophilia may have a special event menus to get a special rewards usable within that event menu, which themselves can be used to be traded back with main rewards

### Rewards

There are many items in s&cardiophilia useful for but not limited to:

- Multiplier Upgrades
- Gacha your new characters. Using gacha tokens or premium coins in game. Sorry, cannot use Talenta of MultiTalent due to s&cardiophilia is not on MultiTalent publication, rather it's on s&box platform.
- System module Unlocks
- Specific Event Menu items. Expiry of an event will cause these items melt into regular items, i.e. Steth Coins (as usually most games would've been Upgrade Cost currencies such as Dennies in ZZZ, Pts in MultiTalent, Dorra in Stella Sora, Credit in Blue Archibe, etc.).

## Lore

DNB is researching sciences recently as they've just successfully established themselves anew for the better world. There are so many stuffs needed to be done, including this one.

The s&cardiophilia initiative was established as a research in wake of severe dillemma after an incident back in mid 2023s (Godot gone woke), among other political conflicts.  
Here, the Realizers who was involved, found s&box from Facepunch. It is also Open Source and Facepunch promises that this engine on Steam will later to be set as Gratis when Garry being the CEO, decides it's time. Therefore they went to work and scoured what should be the premiere trial to make portofolio of. And long short, they decided to retell tales of what Kaorfa's (Joel) adored since long, Heartbeat Cardiophilia.

Taking place 2 centuries later, 2200s, you play as a handler to the characters in this game. After registration, DNB rents you a Protagonist that bridges your interaction to the Characters you'll be observing throughout the game. This was set that it's the only way allowed.

There you can interact with the characters, mess around, and find out new stuffs and even secrets

### Protagonist

The Protagonist Character you get borrowed this time are full chosen by DNB unlike most gacha games.

In first season, you'll be rented a surreal man named `Pondrance`, to observe cute female characters.  
Then in second season, you return Pondrance (because intership over and you got laid off due to distrust), re-register internship again, and be rented his older sister, also surreal, a surreal woman named `Cuddles`. Yep, **to observe cute male characters**.

### Distrusts

After Kaorfa was betrayed, DNB put such a strict rule of how you'd interact Characters in this contract in this game. You will be shown the curious stories alongside others of how and why it's like this, and made curious if leniency reward could be possible.

### Entering Dream

DNB's provided bed in your bedroom serves as a Dream injector where you experience through adventures pertaining to the world around you.

### Touching Grass

But sometimes, even tho you started story from the Bed, some levels need you to go outside.  
Caveat is, since you, the Steam account (you used to login to s&box) that control the Protagonist, is completely distrusted, you have to stay inside. And your Protagonist ensures that you staying inside. Instead, now your selected Character be the one touching grass with audio video feeds provided. Just like ZZZ before Proxies obtained stability, but again a different background as we speak.

## Level Design

### Start Game

Your init scene once the game successfully downloaded & loaded. Inspired from Gacha games init scene.

1. Game started
2. `Powered by s&box` fan animation logo, inspired from many Source games intro
3. `Pinball Agung Indonesia` logo
4. Login screen, with Region selection and `Login` button. Since ~~s&box is only EU-Global~~ currently the save is on your disk (`s&box/data/perkedel/sexy-girl-stething`), the Region selection is not added.

### Registration

When you started this game for the first time, the `Login` button is your registration. Once you clicked that, a new save is created based on your Steam account you logged your s&box in. Then, a desk erects from the ground with the registration form where you just have to confirm all your details. Sign & submit this paper to begin your internship at s&Cardiophilia.

### Main Menu Level

Once you

- logged in again
- completed prologue

You'll arrive in this top down 3d view of the family room in this wide house of yours. Here you can overview your characters wandering around and doing something they like.

#### Decorations

You can buy facilities and place them anywhere valids. The Characters can then interact and gives various curiously effects on their heart organs.

#### Manipulations

Once you have unlocked the Manipulations kit (Adrenaline, Slow, Defib & auto CPR harness, etc.) you can choose 1 character to be messed with and get curious results on their hearts

### Story Levels

Every story is load another Scene, with some load another Scene as an intance GameObejct for it which houses background level for the presentation you will enjoy for.

Each story level have differing numbers of Characters in the GameObject tree, and all hearts within count toward Cookie Clicking. Again, only these Characters appeared here will count, cannot count your current characters you had until you returned to Main menu.

#### Special Events Level

Some special event may have levels on its own.

## Visual Audio Design

## UI-UX

s&cardiophilia UI-UX is built on click menu interface ideology, alike of Blue Archive, Stella Sora, FGO, etc., with some levels do use locomotionings like ZZZ and many typical 3D movement games.

### States

TODO: state machine graph of how menu be like

#### Menuing

Here is the State machine of overall Menu basically would be like:

![Menuing Flow Chart of `Basically`](/src/LibreOffice/sANDcardiophilia-flows-Basically.png)

- Home Menu
  - Bed
  - Special Events
- Story Quest

#### Story Level

![Story level Flow Chart](/src/LibreOffice/sANDcardiophilia-flows-Story.png)

## Tech and Tools

s&cardiophilia in its story also tells meta about the tech involved, as follows:

- s&box. Game Engine, from Facepunch. Known for games like Rust, Garry's mod. s&box under the hood is based on Source 2, but it has been stripped down and instead uses .NET (C#) to script
- C#. Scripting. Because s&box uses .NET as its scripting backend. While different syntax It is almost similar to Unity, you should feel familiar.
- Blender. 3D Modeling. Blender is a Gratis, Open Source, & Full version 3D modeling suite. It allows you model various shapes of mesh with its powerful tools. You can enhance it with addons. All modeling work will use Blender as a standard here in Perkedel Technologies. And for s&box, models will need to be exported to FBX, Z up, and then further processed there.
- Tools of your choice. We recommend that contributors to use Gratis, Open Source, & Full version tool as all as possible, to ensure seamless collaborations.

## Financing

### Monetization

in s&box, developers will be rewarded based on how popular their items are, with an official program called `Play Fund`. How it works as follows:

- Fill all required details
- Must be popular enough. Meaning your game must be played by enough numbers of gamers / Citizen before this term is completed.
- Must be licensed to you. Items must be either from yours, or if from somebody else, you have permission to commercialize it (best if automatic such as license that lacks `NC` (No Commercial), otherwise you had to negotiate, ew!)

### Employment Status as the consequences

Since Play Fund will not be available until above terms and conditions are met, all Contributors to work on this project will be considered as **Tier 0, `Volunteer`****. Meaning you will get 0 salary until said Play Fund becomes available, **&** the money has been transfered to our company's pool where it shall be split across all Contributors in this Organization.

## Sauce

- Use the following help, pls do not use robots! I'll handle this.
  - https://ptik.unima.ac.id/id/blog/game-design-document-gdd-dalam-multimedia-blueprint-penting-pengembangan-game
    
## End

by JOELwindows7  
Perkedel Technologies  
CC4.0-BY-SA
    