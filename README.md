# synth-proto

Browser-based modular node synthesizer built on the Web Audio API. Single self-contained HTML file — no build step, no dependencies.

## Running

Requires Python 3 (pre-installed on most systems).

```bash
cd ~/Projects/synth-proto
python3 -m http.server 9001
```

Then open: **http://localhost:9001**

To keep it running in the background:
```bash
python3 -m http.server 9001 &
```

## Node Types

| Category | Nodes |
|---|---|
| Sources | Oscillator, Noise, Sequencer |
| Effects | Gain, Filter, Delay, Reverb, Distortion, Compressor, Mixer |
| Modulators | LFO |
| Outputs | Speaker, Oscilloscope |

## Usage

- **Drag** a node from the palette to the canvas
- **Drag** from a port dot to connect two nodes
- **Drag** an existing wire to rewire it — drop on empty space to delete
- **Scroll** over any number field to adjust its value
- **▶ Play** starts the audio engine; **■ Stop** tears it down cleanly
- **Auto Arrange** fits all nodes neatly in the viewport
- **VOL** slider in the toolbar controls master volume

## Modulation

Wire LFO `mod` → Filter `freq_mod` to sweep the filter cutoff.  
Wire Sequencer `freq` → Oscillator `freq` to sequence pitch.  
The Mixer node has three named inputs: `ch1`, `ch2`, `ch3` — each with its own gain.

## Presets

Five built-in presets (Drone, Wobble Bass, Space Echo, Fuzz Lead, Arp Sequencer).

**Save As…** saves the current patch (nodes, wires, positions) to `localStorage`.  
**Save** updates the active preset in place.  
**Delete** removes the active user preset.  
Saved presets persist across page refreshes but are tied to the browser/origin.

## Architecture

Everything lives in `index.html` — CSS, HTML, JavaScript. No backend.  
The Python server is just a static file host. ~1250 lines total.
