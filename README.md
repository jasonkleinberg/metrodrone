# MetroDrone

A web-based metronome and drone practice tool designed for musicians who need accurate tempo alongside a reference pitch drone. Perfect for fiddle players, vocalists, and anyone practicing with a steady pitch reference.

## Live Demo

**[Try MetroDrone](https://jasonkleinberg.github.io/metrodrone/)**

## Embed on Your Website

Use this iframe code to embed MetroDrone on your website:

```html
<iframe src="https://jasonkleinberg.github.io/metrodrone/"
        width="100%"
        height="620px"
        style="border: none;">
</iframe>
```

For taller containers with more headroom:

```html
<iframe src="https://jasonkleinberg.github.io/metrodrone/"
        width="100%"
        height="680px"
        style="border: none;">
</iframe>
```

## Features

- **Adjustable Metronome** - Set tempo from 40-200 BPM with both number input and slider
- **Drone Options**:
  - MP3 (Recorded) - High-quality pre-recorded drone sounds with seamless crossfade looping
  - Synth - Warm Pad - Rich synthesized drone with octave doubling for thickness
- **12 Chromatic Keys** - Drones available in all 12 chromatic notes (C, C#, D, Eb, E, F, F#, G, Ab, A, Bb, B)
- **Independent Volume Controls** - Separate sliders for drone and metronome volume
- **Keyboard Shortcut** - Press spacebar to start/stop playback
- **Mobile-Friendly** - Responsive design works on desktop and mobile devices
- **Beautiful UI** - Gradient animated background with smooth controls

## How to Use

1. **Set Your Tempo** - Use the slider or type in a BPM value (40-200)
2. **Choose a Drone Source** - Select MP3 (Recorded) or Synth - Warm Pad
3. **Pick Your Root Note** - Choose from 12 chromatic keys
4. **Adjust Volumes** - Use the drone and metronome volume sliders to balance the mix
5. **Press Start** - Click Start button or press spacebar to begin
6. **Press Stop** - Click Stop button or press spacebar to stop

## Technologies Used

- **HTML5/CSS3/JavaScript** - Core web technologies
- **[Tone.js](https://tonejs.github.io/)** - Web Audio framework for synthesis and audio playback
- **Web Audio API** - For precise audio timing and synthesis
- **GitHub Pages** - Free hosting for the live app

## Recent Improvements

- Raised Warm Pad synth pitch by one octave for better range and reduced distortion
- Added octave doubling to Warm Pad for thicker, richer sound
- Removed Pure Sine option (can be re-added if needed)
- Increased synth volume to better match MP3 recordings
- Significantly boosted metronome volume (36x multiplier) to compete with continuous drones
- Fine-tuned Warm Pad to be 30% quieter than base volume to match MP3 level
- Implemented seamless crossfade looping for MP3 drones

## Adding New MP3 Drone Sounds

If you want to create and add new drone recordings (e.g., Tambura, different instruments, or custom sounds):

### Step 1: Prepare Your Audio Files

1. **Record or source your drone sounds** for each of the 12 chromatic notes
2. **Export as MP3** with these specifications:
   - Format: MP3
   - Sample Rate: 44.1kHz or 48kHz
   - Bit Rate: 192-320 kbps recommended
   - Duration: 10-15 seconds minimum (longer is better for smoother loops)
   - Ensure the audio loops seamlessly (fade in/out at endpoints or use seamless loop editing)

3. **Name your files** using this exact format:
   ```
   drone_C.mp3
   drone_C#.mp3
   drone_D.mp3
   drone_Eb.mp3   (note: Eb, not D#)
   drone_E.mp3
   drone_F.mp3
   drone_F#.mp3
   drone_G.mp3
   drone_Ab.mp3   (note: Ab, not G#)
   drone_A.mp3
   drone_Bb.mp3   (note: Bb, not A#)
   drone_B.mp3
   ```

   **Important:** Use `Eb`, `Ab`, and `Bb` for the flat notes (not `D#`, `G#`, `A#`)

### Step 2: Add Files to Repository

1. **Replace existing MP3 files** - Simply replace the current `drone_*.mp3` files in the root directory with your new recordings
2. **Keep the same filenames** - The app expects these exact filenames
3. **Ensure all 12 notes are present** - Missing notes will cause the app to fall back to the synth

### Step 3: Test Locally

1. **Start a local web server**:
   ```bash
   cd /path/to/metrodrone
   python3 -m http.server 8000
   ```
2. **Open in browser**: `http://localhost:8000`
3. **Test each key** to ensure all MP3s load and loop smoothly
4. **Check volume levels** - Ensure all notes have similar volume

### Step 4: Adjust Volume (Optional)

If your recordings are quieter or louder than the current ones, you may need to adjust the gain multiplier in `index.html`:

1. Open `index.html` in a text editor
2. Find this line (around line 625):
   ```javascript
   const gain = (sliderValue / 100) * 2.0;
   ```
3. Adjust the `2.0` multiplier:
   - Increase (e.g., `3.0`) for quieter recordings
   - Decrease (e.g., `1.5`) for louder recordings

### Step 5: Deploy

1. **Commit your changes**:
   ```bash
   git add drone_*.mp3
   git commit -m "Add new drone recordings"
   git push
   ```
2. **Wait a few minutes** for GitHub Pages to rebuild
3. **Test the live site**: https://jasonkleinberg.github.io/metrodrone/

### Audio Editing Tips

- **For seamless loops**: Use audio editing software (Audacity, Ableton, Logic Pro) to create perfect loop points
- **Normalize volume**: Use audio normalization to ensure consistent volume across all 12 notes
- **Remove DC offset**: Ensure clean audio with no DC bias
- **Crossfade technique**: Add a 2-4 second crossfade region at loop points for ultra-smooth transitions

## File Structure

```
metrodrone/
├── index.html              # Main application file (HTML/CSS/JavaScript)
├── drone_A.mp3            # MP3 recordings for each key
├── drone_Ab.mp3
├── drone_B.mp3
├── drone_Bb.mp3
├── drone_C.mp3
├── drone_C#.mp3
├── drone_D.mp3
├── drone_E.mp3
├── drone_Eb.mp3
├── drone_F.mp3
├── drone_F#.mp3
├── drone_G.mp3
├── MetroDrone_2.png       # Logo image
└── README.md              # This file
```

## Development

This app was built with assistance from Claude Code. The entire application is contained in a single `index.html` file for easy deployment and sharing.

### Local Development

1. Clone the repository
2. Start a local web server (required for MP3 loading):
   ```bash
   python3 -m http.server 8000
   ```
3. Open `http://localhost:8000` in your browser
4. Make changes to `index.html`
5. Refresh browser to see changes

## Credits

- Built with [Tone.js](https://tonejs.github.io/) by Yotam Mann
- Logo design: MetroDrone_2.png
- MP3 drone recordings: Custom recordings
- Developed with assistance from Claude Code

## License

This project is open source and available for personal and educational use.

## Contributing

Feel free to fork this repository and submit pull requests with improvements! Suggestions for new features are welcome.

## Support

For questions or issues, please open an issue on GitHub.

---

**Enjoy practicing with MetroDrone!**
