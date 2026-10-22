# Knightfall

A 2D action RPG built with Unity. It has two stages, several enemy types, power-ups and a final boss.

This game is a prototype for a 2D RPG with the basic mechanics in place: movement, combat, buffs and animations. I plan to add more features, or make a part 2, to build on it.

## Features

- **Platforming movement:** run, jump, wall slide, wall jump and dash.
- **Melee combat:** a basic attack combo, jump attacks, and a **counter-attack** that stuns enemies when timed right.
- **Elemental damage:** Fire, Ice and Lightning, with status effects (burn, chill and lightning strikes).
- **Stats system:** major, offense, defense and resource stat groups, set up with ScriptableObjects.
- **Skill tree:** spend skill points to unlock skills, such as the dash, from an in-game skill tree with tooltips.
- **Enemies:** skeletons, slimes and zombies, each with idle, move, battle, attack, stunned and death states. Enemies have health bars and drop items.
- **World objects:** chests, buff pickups, portals between levels and parallax backgrounds.
- **Game flow:** title screen, main menu, pause menu, options, game over screen and background music.

## Controls

| Action | Key |
|---|---|
| Move | `W` `A` `S` `D` |
| Jump | `Space` |
| Attack | Left mouse button / `J` |
| Dash | `Left Shift` |
| Counter-attack | `Q` |
| Skill tree | `L` |
| Pause menu | `Esc` |

## Architecture

- **Finite state machine:** the player and enemies are driven by a shared `StateMachine`. Each behavior (idle, move, jump, attack, dash, wall slide, stunned, dead and so on) is its own state class.
- **Entity base class:** `Entity` handles shared logic, with separate components for health, combat, stats, status effects, VFX and drops. `Player` and `Enemy` build on it.
- **Interfaces:** `IDamagable` and `ICounterable` decouple combat interactions.
- **ScriptableObjects:** stats, skills and items are defined as data assets, so balancing doesn't require code changes.
- **New Input System:** controls are defined in an input action asset (`PlayerInputSet`).

```
Assets/Scripts/
  StateMachine/     generic state machine + player/enemy base states
  Player/           player controller and states
  Enemy/            enemy base, skeleton/slime/zombie, enemy states
  Entity/           shared health, combat, stats, status effects, VFX, drops
  StatsSystem/      stat groups and stat setup
  SkillSystem/      skill base, dash skill, skill data
  UI/               HUD, health bars, skill tree, tooltips, pause, options
  InteractionObjects/  chests and buffs
```

## Getting started

1. Install **Unity 6** (6000.0.38f1) with Unity Hub.
2. Clone the repo and open the folder in Unity Hub.
3. Open `Assets/Scenes/TitleScreen.unity` and press **Play**.

## Tech stack

Unity 6 · C# · Universal Render Pipeline (2D) · Unity Input System

## Credits

I do not own any of the sprites used in this project. All art belongs to its original creators.
