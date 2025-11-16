# Quick Reference - Rich Text Tags

## Available Tags for Dialogue

### Text Colors
```
<c=red>danger text</c>
<c=blue>water text</c>
<c=green>nature text</c>
<c=yellow>highlight text</c>
<c=purple>magic text</c>
```

### Text Formatting
```
<b>bold emphasis</b>
<large>BIG TEXT</large>
<small>tiny text</small>
```

### Text Animations
```
<wave>flowing text</wave>      - Gentle up/down motion
<shake>trembling text</shake>  - Rapid shaking
<glitch>corrupted</glitch>     - Random character swap
```

### Combining Tags
```
<c=red><b>CRITICAL WARNING</b></c>
<wave><c=blue>Mystical Waters</c></wave>
<shake><c=yellow>DANGER</c></shake>
```

## Example Dialogue

```javascript
dialogue.push({
  speaker: "Ancient Guardian",
  text: "<wave>Welcome, traveler.</wave> I sense <c=red><b>great danger</b></c> ahead.",
  flavor: "<c=purple>Their eyes glow with ancient power.</c>"
});

dialogue.push({
  speaker: "Shopkeeper",  
  text: "These <c=yellow>rare items</c> are <large>expensive</large>, but <shake>powerful</shake>!",
  flavor: "<c=green>They rub their hands together eagerly.</c>"
});

dialogue.push({
  speaker: "System Error",
  text: "<glitch>DATA CORRUPTED</glitch> - <c=red>SYSTEM FAILURE</c>",
  flavor: "<shake><c=red>WARNING: UNSTABLE</c></shake>"
});
```

## Controls Reminder

- **E** - Interact / Advance Dialogue / Close Shop
- **Click during dialogue** - Complete typewriter instantly
- **Click again** - Advance to next dialogue
- **I** - Open/Close Full Inventory
- **ESC** - Close Inventory

## Time Scale Examples

```javascript
// Browser console commands:
GAME_TIME_SCALE = 0.5;  // Matrix bullet-time
GAME_TIME_SCALE = 0.25; // Super slow-mo
GAME_TIME_SCALE = 2.0;  // Speed run mode
GAME_TIME_SCALE = 0.0;  // Pause everything
GAME_TIME_SCALE = 1.0;  // Back to normal
```
