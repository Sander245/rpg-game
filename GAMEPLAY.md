# How to Play - Advanced Metroidvania Demo

## Starting the Game

1. Open `infgame.html` in any modern web browser
2. Click anywhere to start audio (required for Web Audio API)
3. You'll hear a melodic chord progression (calm exploration music)

## Basic Controls

- **W / Space / ↑** - Jump
- **A / D / ← / →** - Move left/right  
- **Shift** - Dash (enhanced with "longerDash" upgrade)
- **J** - Attack (melee by default)
- **E** - Interact (talk to NPCs, open shops, collect items)
- **I** - Open/Close full inventory screen
- **Esc** - Close menus

## First Steps

### 1. Collect Upgrades
- Jump across platforms to find **Pulse Leaf** (🍃) - enhances jump height
- Find **Dash Prism** (💨) - extends dash distance
- Press **E** near items to collect them

### 2. Gather Currency
- Collect **Echo Coins** (🪙) - worth 50 Echoes each
- Defeat enemies - they drop 20 Echoes on death
- You start with 100 Echoes

### 3. Visit the Shop
- Find **Archivist Lyra** (blue character near the start)
- Press **E** to open shop
- Available items:
  - **Crystal Blade** (⚔️) - Sword, 150 Echoes, +10 ATK
  - **Phase Bow** (🏹) - Bow, 180 Echoes, +8 ATK, ranged
  - **Vault Plate** (🛡️) - Armor, 120 Echoes, +8 DEF, +25 HP
  - **Sprint Ring** (💍) - Accessory, 80 Echoes, +1.2 Speed
  - **Fire Gem** (🔥) - Weapon upgrade, 60 Echoes, +10 DMG (sword only)
  - **Range Crystal** (💠) - Weapon upgrade, 50 Echoes, +15 range

### 4. Equip Items
- Press **I** to open inventory
- **Drag items** to equipment slots (Weapon / Armor / Accessory)
- Watch your stats update in the HUD: `ATK:X DEF:Y`
- If you equip a weapon with upgrade slots, you'll see the upgrade grid below

### 5. Add Weapon Upgrades
- Buy upgrade gems from the shop
- With weapon equipped, upgrades appear in inventory
- Some upgrades only work with specific weapons (Fire Gem = sword only)
- Drag upgrades to the weapon upgrade slots (circles below equipment)

## Combat System

### Fighting Enemies

**Gleam Spore** (pink, 40 HP)
- Patrols platforms
- Chases you when close
- Can jump to reach you

**Arc Sentinel** (pink, 55 HP)  
- Patrols and chases
- **Shoots projectiles** when in range
- Jumps to pursue

**Phase Scout** (pink, 45 HP)
- Faster movement (2.0 speed)
- Aggressive chase behavior

### Combat Tips
- Watch enemy **HP bars** above their heads
- Green = healthy, Yellow = wounded, Red = low HP
- Use **Shift-dash** to dodge ranged attacks
- Enemies drop **💎 Cores** + **20 Echoes** on death

### Weapon Comparison
- **No weapon**: 15 base damage, 28 range
- **Crystal Blade**: 40 damage (25+10+5 from stats), 35 range, melee arcs
- **Phase Bow**: 33 damage (18+8+5), 120 range, would shoot projectiles (not fully implemented)

## Checkpoint System

Blue glowing squares are **checkpoints**:
- Walk through them to activate (turns brighter blue)
- Your position, HP, and currency are saved
- If you **fall off the map**, you'll:
  - Lose 20 HP
  - Respawn at last checkpoint after 0.5 seconds
  - Screen shakes on respawn

**Checkpoints in demo:**
- Near start (x=100)
- Mid-level (x=800)  
- End vault (x=1420)

## Special Zones

### Camera Zoom Trigger
- Around x=750 - camera zooms to 1.2x
- Creates cinematic focus

### Shake Trigger  
- Around x=1150 - screen shakes (intensity 6)
- Simulates environmental hazard

## Audio Features

Listen for:
- **Calm music** - Chord progression (Am → Bdim → C → Dm) with vibrato
- **Battle music** - When enemies hit you, arpeggio + bass + kick drum kicks in
- **Softer sounds** - Damage/pickup sounds at 60-70% volume (less annoying!)
- **Spatial audio** - Enemy hit sounds pan left/right based on position

## Inventory Management

Press **I** to open:
- **Left side** - Equipment slots (Weapon/Armor/Accessory)
- **Right side** - Item grid
- **Bottom** - Currency display
- **Weapon upgrades** - Shows below equipment when weapon equipped

### Drag & Drop
1. Click and hold on item in grid
2. Drag to equipment slot
3. Release to equip
4. Click equipped item to unequip

## Advanced Techniques

### Speed Running
- Equip **Sprint Ring** (+1.2 speed)
- Use **longerDash** upgrade
- Chain dash jumps across platforms

### Tank Build  
- Equip **Vault Plate** (+8 DEF, +25 HP = 125 total HP)
- Defense reduces incoming damage
- Survive more hits

### Damage Build
- Equip **Crystal Blade** base damage
- Add **Fire Gem** (+10 damage, sword only)
- Total: 50+ damage per hit

## Level Layout

```
Start → Platforms → Shop (Lyra) → Mid Checkpoint → Enemies → Vault → End
 100      200-500       170           800           900-1500    1650
```

## Tips & Tricks

1. **Save before shopping** - Activate checkpoint before spending Echoes
2. **Farm enemies** - Each enemy respawns (in this demo) for currency
3. **Explore high platforms** - Upgrades often hidden above
4. **Watch HP bars** - Know when enemies are almost dead
5. **Use environment** - Jump between platforms to avoid ranged attacks

## Troubleshooting

**No music?**
- Click on the game canvas to start audio context
- Check browser console for errors

**Can't open inventory?**
- Press **I** (not E)
- Make sure you're not in a cutscene

**Shop won't open?**
- Stand right next to Archivist Lyra
- Press **E**
- Check if you see blue character at x=170

**Items won't equip?**
- Make sure you're dragging to correct slot
- Weapons go to "Weapon" slot only
- Armor goes to "Armor" slot only

## Have Fun!

This demo showcases 18+ advanced features in a single HTML file. Experiment with different equipment combinations, test the AI, and explore the camera effects. The entire game runs client-side with no server required!
