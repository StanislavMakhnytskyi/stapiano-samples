# StaPiano piano samples

Compressed piano sample sets used by the StaPiano app. Each instrument lives in its own folder:

```
<id>/<midi>_<layer>.m4a    e.g. steinway-b/60_v3.m4a   (MIDI 21 = A0, 60 = C4)
<id>/manifest.json         { id, notes, layers: [{ id, minVelocity }], preloadLayer, sourceUrl, license }
```

Layers `v1`, `v2`, ... run from soft to loud. Only the first round robin (`rr1`) of each source is used.

## Encoding (all files)

Mono, AAC (.m4a), 96 kbps, 44.1 kHz. Each sample is trimmed to at most 10 s with a 0.4 s fade-out, and leading silence below -60 dB is removed (the attack is kept). For very quiet source files whose peak is below -60 dB, the threshold is relaxed to 30 dB under the file's own peak so the sample is not erased.

## Instruments

| id | Instrument | Notes | Layers | Source | License |
|---|---|---|---|---|---|
| `steinway-b` | Steinway B grand | 42 (MIDI 22-104, whole tones) | 3 | VCSL | CC0 |
| `kawai-grand` | Kawai grand | 33 (MIDI 24-108, irregular) | 4 | VCSL | CC0 |
| `upright` | Knight upright | 45 (MIDI 21-107 odd numbers, plus 108) | 2 | VCSL | CC0 |
| `yamaha-c5` | Yamaha C5 (Salamander Grand Piano V3) | 30 (MIDI 21-108, minor thirds) | 4 | Salamander | CC BY 3.0 |

### steinway-b
Source: Versilian Community Sample Library, `Chordophones/Zithers/Grand Piano, Steinway B/NoSus/` (files `JHPiano_NoSus_Close_*`), close mics, no sustain pedal. License CC0.
Processing: layers `vl2`, `vl3`, `vl4` become `v1`, `v2`, `v3`. The source layers are normalized to equal loudness, so dynamics were restored by attenuating the softer layers by -12 dB (v1) and -6 dB (v2); v3 is unchanged.

### kawai-grand
Source: Versilian Community Sample Library, `Chordophones/Zithers/Grand Piano, Kawai/Sustains/` (not the Legacy folder). License CC0.
Processing: layers `v1`-`v4` kept as is (they have natural dynamics; no gain change). File names use an octave number one lower than standard, so the octave is shifted by +1 (file `C0` is MIDI 24). Notes that are missing from some layers (MIDI 22, 82, 83, 102, 103) were dropped so all layers share one note list. Note that `v1` is very quiet (peaks around -40 to -55 dBFS).

### upright
Source: Versilian Community Sample Library, `Chordophones/Zithers/Upright Piano, Knight/Sustains/`, sampled by Simon Dalzell of Ivy Audio for the VSCO 2 Pro sample set. License CC0.
Processing: only two velocity layers exist (`vl1`, `vl2` become `v1`, `v2`), kept at natural level. Sampled in whole tones from the instrument's low A; the source's pitch chart maps the files to MIDI 21, 23, ... 107, 108 (file `A-1` is MIDI 21). With two layers `v2` starts at velocity 64 rather than 110.

### yamaha-c5
Source: [Salamander Grand Piano V3](https://github.com/sfzinstruments/SalamanderGrandPiano) (Yamaha C5), recorded by Alexander Holm. License: [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/).
Processing: a subset of the original release, already encoded as mono AAC 96 kbps; 30 notes (A0 to C8, minor-third spacing) and original velocity layers 3, 7, 11, 15, renamed `v1`-`v4`. Copied without re-encoding.

See `LICENSE.md` for licensing and attribution details.
