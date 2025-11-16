# Infinite Game Preset

A lightweight browser-based 2D platformer / metroidvania starter built with vanilla HTML5 canvas and JavaScript. It ships with parallax backgrounds, basic physics, combat, dash/jump upgrades, NPC dialogue with flavor text, pickups, cutscenes, and an inventory overlay so you can drop in new content quickly.

## Run It

1. Open `infgame.html` in any modern desktop browser (Chrome, Edge, Firefox). No build step is required.
2. Play with the bundled demo scene or wire in your own level data via the exposed preset API.

## Controls

| Action | Keys |
| --- | --- |
| Move | `A` / `D` or `←` / `→` |
| Jump | `W`, `Space`, or `↑` |
| Dash | `Shift` |
| Attack | `J` |
| Interact / Advance dialogue | `E` |
| Toggle inventory panel | `I` |

## Extending Quickly

The script exports `window.PlatformerPreset` for convenience:

- `PlatformerPreset.start(levelData?)` – boots the engine with the provided level JSON or the bundled example.
- `PlatformerPreset.utils.platform(x, y, width, height)` – helper to define a platform rectangle.
- `PlatformerPreset.utils.pickup(name, description, x, y, upgradeKey?)` – helper to define collectible items.
- `PlatformerPreset.exampleLevel` – clone this object to create your own layout.
- `PlatformerPreset.audio` – live audio director with helpers for battle state, healing cues, inventory muffling, and procedural SFX.
- `PlatformerPreset.audioEngine` – lower-level Web Audio mixer if you want to register custom tracks/buses yourself.

`PlatformerPreset.start` returns an API with `addPlatform`, `addNPC`, `addEnemy`, `addPickup`, and `addCutscene` so you can spawn content at runtime.

### Audio Hooks

The preset keeps Web Audio running with calm pads, battle ramps, and inventory muffling. You can drive it manually if you need finer control:

- `PlatformerPreset.audio.enterBattle(reason)` / `.exitBattle(reason)` – fades between calm and combat layers.
- `PlatformerPreset.audio.setInventoryOpen(bool)` – applies a gentle low-pass filter (used automatically when pressing `I`).
- `PlatformerPreset.audio.playHeal(amount)` – sparkly cues for healing or buff pickups.
- `PlatformerPreset.audio.createTrack(name, config)` – registers custom tracks. Pass an object `{ type: "music" | "sfx", volume, effects, generator }` where `generator({ context, input })` wires oscillators/buffers into the provided input node.
- `PlatformerPreset.audio.playNoise(opts)` / `.playTone(opts)` – quick one-shot procedural SFX (white/pink noise, sine/triangle tones, configurable duration/pitch).

Battle music automatically ramps in when enemies or the player land hits, and fades out a few seconds after peace is restored. Opening the inventory muffles the mix, and dash/pickup/heal events trigger unique procedural sounds to keep the preset lively without external assets.

### Level Data Shape

```js
{
  name: "adventure place thingy",
  playerStart: { x: 120, y: 360 },
  backgroundLayers: [ { type: "gradient", colors: ["#050813", "#0a0f1f"], parallax: 0 }, ... ],
  platforms: [ { x: 0, y: 500, width: 1400, height: 60 }, ... ],
  npcs: [ { name: "Archivist Lyra", x: 170, y: 454, dialogue: ["line"], flavor: "blurb" } ],
  enemies: [ { name: "evil guy", x: 420, y: 330, patrol: [360, 520], hp: 40 } ],
  pickups: [ { name: "yes Prism", description: "yes dash", x: 820, y: 248, upgrade: "yesDash" } ],
  cutscenes: [ { id: "intro", trigger: { x: 80, y: 400, width: 80, height: 120 }, steps: [...] } ]
}
```

Cutscene steps support:

- `dialog` – `{ type: "dialog", speaker, text, flavor }`
- `wait` – `{ type: "wait", duration }`
- `camera-pan` – `{ type: "camera-pan", x, y, duration }`
- `grant-upgrade` – `{ type: "grant-upgrade", key, name, description }`

## Notes

- Physics, combat, inventory, and dialogue code live entirely in `infgame.html` for easy copypasta.
- Asset-free parallax layers keep the preset light, but you can swap in sprite rendering inside `drawPlayer`, `drawEnemy`, etc.
- The engine avoids build tooling by design; just edit the HTML file and refresh the browser.
