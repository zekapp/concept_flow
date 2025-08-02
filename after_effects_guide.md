# After Effects Production Guide
## Ship of Theseus Animation

### Project Setup
1. **Composition Settings:**
   - Resolution: 1920x1080
   - Frame Rate: 30fps
   - Duration: 75 seconds
   - Background Color: #87CEEB

### Required Assets

#### Illustrator/Vector Files Needed:
1. **ship_base.ai** - Ship hull and structure
2. **plank_old.ai** - Dark brown plank
3. **plank_new.ai** - Light beige plank
4. **human_silhouette.ai** - Simple human figure
5. **water_waves.ai** - Wave patterns

#### Text Layers:
- Create all text as editable AE text layers
- Font: Montserrat for headers, Open Sans for body

### Layer Structure

```
COMP: Main_Animation
├── PRE-COMP: Scene_1_Intro (0-10s)
│   ├── BG: Sky gradient
│   ├── Water waves (looped)
│   ├── Ship (floating animation)
│   └── Text: "This is the Ship of Theseus"
│
├── PRE-COMP: Scene_2_Replacement (10-30s)
│   ├── Ship base
│   ├── Plank grid (20x10 planks)
│   ├── Replacement animation (null controller)
│   ├── Counter display
│   └── Thought bubble text
│
├── PRE-COMP: Scene_3_TwoShips (30-50s)
│   ├── Dock A with Ship A
│   ├── Dock B with Ship B
│   ├── Assembly animation
│   └── Question text
│
├── PRE-COMP: Scene_4_Human (50-65s)
│   ├── Human silhouette
│   ├── Particle system (CC Particle World)
│   ├── Neuron effects (optional)
│   └── Text layers
│
└── PRE-COMP: Scene_5_Closing (65-75s)
    ├── Ship fade animation
    ├── Question mark morph
    └── Final text + hashtags
```

### Key Animation Techniques

#### 1. Floating Ship Animation
```
Position: Wiggle(2, 5)
Rotation: Wiggle(1, 2)
```

#### 2. Plank Replacement
- Use expressions to control replacement timing
- Array of 200 plank layers
- Sequential opacity animation
- Position offset for "lifting" effect

#### 3. Counter Expression
```javascript
// Apply to Source Text
startCount = 100;
endCount = 0;
duration = 20; // seconds
t = time - 10; // start at 10s
value = Math.round(linear(t, 0, duration, startCount, endCount));
value + "%"
```

#### 4. Particle System Settings
- Birth Rate: 50
- Longevity: 2 seconds
- Velocity: 100
- Gravity: 0
- Particle Type: Line

### Effects and Plugins

#### Essential Effects:
1. **CC Force Motion Blur** - For smooth transitions
2. **Gaussian Blur** - Depth of field
3. **Drop Shadow** - Subtle depth
4. **CC Particle World** - Cell animation
5. **Fractal Noise** - Water texture

#### Color Correction:
- Add Adjustment Layer with:
  - Curves for contrast
  - Color Balance for warm tones
  - Slight vignette

### Animation Timing Sheet

| Time | Action |
|------|--------|
| 0:00 | Fade in from white |
| 0:03 | Title appears |
| 0:05 | Ship fully visible |
| 0:10 | Zoom begins |
| 0:12 | First plank replacement |
| 0:15 | Speed up replacements |
| 0:25 | Thought bubble appears |
| 0:30 | Camera pan to dock B |
| 0:35 | Assembly sequence |
| 0:45 | Both ships side by side |
| 0:50 | Morph to human |
| 0:52 | Particle animation |
| 0:65 | Begin final sequence |
| 0:70 | Question mark formed |
| 0:75 | End card |

### Export Settings

#### Main Export:
- Format: H.264
- Preset: YouTube 1080p HD
- Bitrate: 8-10 Mbps
- Audio: AAC, 320 kbps

#### Additional Exports:
- Instagram: 1080x1080 (square crop)
- Twitter: 1280x720
- GIF: 480p, 256 colors

### Performance Tips
1. Pre-render heavy sections
2. Use proxies for complex compositions
3. Cache preview before final export
4. Purge memory between renders

### Quality Checklist
- [ ] All text is readable
- [ ] Animations are smooth (no jerky movements)
- [ ] Colors are consistent
- [ ] Audio levels are balanced
- [ ] No render artifacts
- [ ] Proper fade in/out
- [ ] Hashtags are visible for 3+ seconds