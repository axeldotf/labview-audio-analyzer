# Time & Frequency Domain Audio Analyzer (LabVIEW)

> A LabVIEW Virtual Instrument for acquiring, playing back and analyzing an audio sample in the **time** and **frequency** domains, with optional low-pass filtering, built in **LabVIEW**.

This repository documents a measurement-instrumentation project: a LabVIEW VI that records a sound sample from a microphone (or loads an existing `.wav`), plays it back, saves it, and performs spectral analysis. The signal can be inspected in the time domain and in the frequency domain (FFT, RMS values), and a tunable low-pass filter lets the user compare the original and filtered waveforms side by side.

Developed as the final project for the **Electronic Measurements** course, B.Sc. in Electronic Engineering, University of Perugia (UNIPG).

---

## What it does

The instrument is organized as a single VI with a guided four-stage workflow on the Front Panel:

- **Acquisition** of a sound sample from the PC's internal or an external microphone, with user-set duration and sample rate.
- **Loading** of a previously recorded `.wav` file.
- **Playback** of the signal through any output device (speakers, headphones).
- **Saving** of the acquired sample to a `.wav` file.
- **Spectral analysis** — time-domain plot and frequency-domain plot (FFT, RMS).
- **Low-pass filtering** with an adjustable cut-off frequency, plotting the filtered signal alongside the original.

---

## Workflow

The Front Panel drives the program through four stages:

| Stage | Name | Description |
| ----- | ---- | ----------- |
| 1 | Record / Analyze | Choose whether to acquire a new sample or analyze an existing `.wav`. Loading a file skips straight to Stage 4. |
| 2 | Acquisition | Set duration and sample rate. Three LEDs signal *ready*, *recording started* and *recording finished*. |
| 3 | Saving | Optional playback, then optional save of the `.wav` to the chosen path. |
| 4 | Analysis | Replay the sample, apply the low-pass filter, and plot original vs. filtered signals in time and frequency. |

The default low-pass cut-off is **100 Hz** and can be changed from the Front Panel; the filter type itself can be reconfigured in the Block Diagram via the `Filter` block.

---

## Implementation notes

The Block Diagram is split into two regions: signal **acquisition/loading** (a Case structure selecting between live recording and `.wav` load) and signal **analysis** (playback, spectral measurement, filtering). Core building blocks include:

| Block | Role |
| ----- | ---- |
| Acquire Sound | Captures a sample from the selected input source |
| Play Waveform | Plays the signal through an output device |
| Spectral Measurements | Computes FFT (RMS) and phase for spectral analysis |
| Sound File Read / Write Simple | Loads / saves the sample as a `.wav` waveform |
| Filter | Applies the low-pass filter with the chosen cut-off |
| Flat Sequence / For Loop / Case / Time Delay | Control flow and timing |

---

## Requirements

- **LabVIEW** (2020 or later recommended)
- A microphone (internal or external)
- An audio output device

> The `.vi` file requires LabVIEW to open and run. Make sure your installed version is compatible with the one used to save the VI.

---

## Repository contents

```
.
├── README.md
├── AudioAnalyzer.vi                        # LabVIEW Virtual Instrument
├── Tesina_Misure_Frullo_Corrado.pdf        # Project report (design, block diagram, front panel, user guide)
└── test/                                   # Sample .wav files for testing
    ├── sample1.wav
    └── sample2.wav
```

> The report contains the full walkthrough: LabVIEW basics, project specifications, the Functions used, the Block Diagram and Front Panel, and a step-by-step user guide.

---

## Authors

**Alessandro Frullo** · **Anna Rita Corrado**
B.Sc. in Electronic Engineering — University of Perugia (UNIPG)
Electronic Measurements course project.
