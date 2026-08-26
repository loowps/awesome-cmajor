# Awesome Cmajor [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of awesome resources, tools, patches and projects for [Cmajor](https://cmajor.dev) — a C-family programming language for writing fast, portable audio DSP.

Cmajor is built by [Cmajor Software Ltd](https://cmajor.dev/about-us) (formerly Sound Stacks), founded by Julian Storer, the original author of [JUCE](https://juce.com). It compiles DSP graphs to native code via LLVM or to WebAssembly, runs the same source on CPUs, in DAWs and in browsers, and packages everything as a self-contained *patch* with an optional web-tech GUI.

## Contents

- [Official Resources](#official-resources)
- [Documentation](#documentation)
- [Tools & Editor Support](#tools--editor-support)
- [Official Example Patches](#official-example-patches)
- [Community Patches & Plugins](#community-patches--plugins)
- [Embedding & Integration](#embedding--integration)
- [Machine Learning](#machine-learning)
- [Talks & Videos](#talks--videos)
- [Community](#community)
- [Related Projects](#related-projects)

## Official Resources

- [cmajor.dev](https://cmajor.dev) — Official home page and documentation hub.
- [cmajor-lang/cmajor](https://github.com/cmajor-lang/cmajor) — The main public repository: compiler, command-line tools, C++ API, JavaScript API and examples.
- [Releases](https://github.com/cmajor-lang/cmajor/releases) — Prebuilt binaries for macOS, Windows and Linux.
- [Issue tracker](https://github.com/cmajor-lang/cmajor/issues) — Bug reports, feature requests, and a searchable archive of past answers.
- [cmajor-lang on GitHub](https://github.com/cmajor-lang) — The organisation, including the docs site and dependency forks.
- [Licence terms](https://cmajor.dev/docs/CmajorLicenceTerms) — Read these before shipping a commercial product; the language, tools and runtime are not all covered by the same terms.

## Documentation

- [Getting Started](https://cmajor.dev/docs/GettingStarted) — Install paths, first patch, and the `cmaj` command-line tool.
- [Language Reference](https://cmajor.dev/docs/LanguageReference) — The full language: processors, graphs, streams, events, value types, generics and namespaces.
- [Standard Library](https://cmajor.dev/docs/StandardLibrary) — `std::oscillators`, `std::filters`, `std::envelopes`, `std::notes`, `std::mixers` and friends.
- [Patch Format](https://cmajor.dev/docs/PatchFormat) — The `.cmajorpatch` manifest, resources, GUI folder, and the export routes to CLAP/VST/AU/Web Audio.
- [Test File Format](https://cmajor.dev/docs/TestFileFormat) — Writing `.cmajtest` unit tests for DSP code, run with `cmaj test`.
- [Script File Format](https://cmajor.dev/docs/ScriptFileFormat) — JavaScript-driven build and render scripts.
- [C++ API](https://cmajor.dev/docs/Tools/C++API) — Loading, JIT-compiling and rendering patches from a C++ host.
- [Quick Start (repo copy)](https://github.com/cmajor-lang/cmajor/blob/main/docs/Cmaj%20Quick%20Start.md) — The same guide, versioned alongside the source.

## Tools & Editor Support

- [Cmajor for VS Code](https://marketplace.visualstudio.com/items?itemName=SoundStacks.cmajor) — The official extension: syntax highlighting, one-click toolchain install, `Cmajor: Create a new patch`, and patch playback from the command palette. The fastest way in.
- **`cmaj` command-line tool** — Ships with the release bundle. The workhorse commands:
  - `cmaj play <patch>` — Render a patch live to your audio device.
  - `cmaj test <file.cmajtest>` — Run a DSP test suite.
  - `cmaj generate --target=cpp` — Emit dependency-free C++ that needs no JIT at runtime.
  - `cmaj generate --target=webaudio-html` — Emit a standalone HTML/JS/WASM bundle.
  - `cmaj generate --target=juce` — Emit a JUCE project for a native VST3/AU/AAX build.
  - `cmaj generate --target=clap` — Emit a native [CLAP](https://cleveraudio.org) plugin project.
- [Cmajor VST/AU plugin](https://cmajor.dev/docs/GettingStarted#loading-patches-in-your-daw-with-the-cmajor-vstau-plugin) — A host plugin that loads and hot-reloads `.cmajorpatch` files inside any DAW, so you can iterate on DSP without restarting the session.

## Official Example Patches

All of these live in [`examples/patches`](https://github.com/cmajor-lang/cmajor/tree/main/examples/patches) and are catalogued at [cmajor.dev/docs/Examples](https://cmajor.dev/docs/Examples).

- **HelloWorld** — The smallest possible patch. Start here.
- **Tremolo** — Minimal modulation effect, and the basis of the ADC workshop below.
- **RingMod** — Ring modulator paired with a hand-written GUI.
- **FilterEQ** and **PirkleFilters** — Filter design, including ports from Will Pirkle's books.
- **ZitaReverb** — A port of the well-known Zita reverb algorithm.
- **808** — Classic drum machine voice synthesis.
- **Piano** and **ElectricPiano** — Physically-inspired and sample-driven instruments.
- **TunedBar** — Modal synthesis of a struck bar.
- **[Pro54](https://github.com/cmajor-lang/cmajor/tree/main/examples/patches/Pro54)** — A full polyphonic analogue-style synth, and the flagship demonstration of what the language can do at scale.
- **GuitarLSTM** — Neural amp modelling running inside a patch.
- **Replicant** — Port of the Maximilian example of the same name.
- **CompuFart** — Yes, really. See the community repo below.

## Community Patches & Plugins

- [alexmfink/compufart](https://github.com/alexmfink/compufart) — A fart synthesizer and the algorithm behind it. Genuinely instructive, and the origin of the official example.
- [lilyvanoekel/percupuff](https://github.com/lilyvanoekel/percupuff) — Drum synthesizer with a TypeScript/React UI, building to CLAP, VST3, a standalone binary or WebAssembly. One of the best end-to-end references for how to structure a real project.
- [lilyvanoekel/Oscilluna](https://github.com/lilyvanoekel/Oscilluna) — Creative synth with user-designable waveforms, shipping as VST3 and CLAP.
- [olilarkin/cmajor_pirklefilters](https://github.com/olilarkin/cmajor_pirklefilters) — Will Pirkle's filter designs ported to Cmajor.
- [olilarkin/cmajor_replicant](https://github.com/olilarkin/cmajor_replicant) — Port of the Maximilian "replicant" example.
- [loowps/cmajor-orrery](https://github.com/loowps/cmajor-orrery) — Polymetric, variable-step-size MIDI sequencer with a Vue UI.
- [loowps/cmajor-angular](https://github.com/loowps/cmajor-angular) — Gain patch with an Angular GUI compiled to a single web component.
- [loowps/cmajor-vue](https://github.com/loowps/cmajor-vue) — The same idea in Vue.js, built as a CLAP.
- [`#cmajorpatch` on GitHub](https://github.com/topics/cmajorpatch) — Tag your own patch repositories with this topic so others can find them.

## Embedding & Integration

- [C++ API](https://cmajor.dev/docs/Tools/C++API) — Embed the JIT engine in a host app, or use `cmaj::JUCEPluginFormat`, a `juce::AudioPluginFormat` that scans for and loads patches as though they were plugins.
- [Ahead-of-time C++ generation](https://cmajor.dev/docs/PatchFormat#building-a-native-juce-vst-or-audiounit-from-a-patch) — `cmaj generate --target=cpp` translates Cmajor into plain C++ with no runtime dependency on the compiler. This is the route to embedded targets and locked-down plugin formats.
- [Web Audio / WebAssembly export](https://cmajor.dev/docs/PatchFormat#exporting-a-patch-as-javascriptwebassemblyweb-audio) — Emit a dependency-free HTML/JS bundle, or take just the JS classes and wire them into an existing site.
- [`cmaj_api` JavaScript helpers](https://github.com/cmajor-lang/cmajor/tree/main/javascript/cmaj_api) — `patchConnection` and friends: the bridge between a patch's parameters and events and a web GUI.
- [free-audio/clap-wrapper](https://github.com/free-audio/clap-wrapper) — Wraps a CLAP into VST3/AU. Used by Cmajor's CLAP export path.
- [cmajor-lang/clap-example](https://github.com/cmajor-lang/clap-example) — A worked example of building the Pro54 synth as a CLAP plugin.

## Machine Learning

- [Machine Learning docs](https://cmajor.dev/docs/Tools/MachineLearning) — Running inference inside a patch, with the supported operator lists for each backend.
- **ONNX support** — Import models exported from PyTorch or TensorFlow via ONNX.
- [RTNeural](https://github.com/jatinchowdhury18/RTNeural) — Real-time-safe neural inference library, supported as a Cmajor backend.
- [cmajor-lang/GuitarLSTM](https://github.com/cmajor-lang/GuitarLSTM) — LSTM amp and pedal emulation models, the source of the GuitarLSTM example patch.

## Talks & Videos

- [SoundStacks' New Cmajor Platform](https://www.youtube.com/watch?v=qGVyaEVH0o0) — ADC22. Julian Storer, Cesare Ferrari, Lucas Thompson and Harriet Drury introduce the language and the platform. The best single starting point.
- [Introduction to Cmajor & SoundStacks](https://www.youtube.com/watch?v=FHtahCOBfgo) — Julian Storer and Cesare Ferrari with The Audio Programmer.
- [cmajor-lang/ADC23_workshop](https://github.com/cmajor-lang/ADC23_workshop) — The tremolo example code from the ADC 2023 Cmajor workshop, so you can follow along from scratch.
- [WolfTalk #032: Julian Storer](https://thewolfsound.com/talk032/) — Long-form interview with the creator of JUCE, covering the thinking that led to Cmajor.

## Community

- [Cmajor channel on The Audio Programmer Discord](https://discord.gg/Abtc5xabcT) — Channel where the core team can be reached.
- [KVR Audio DSP forum thread](https://www.kvraudio.com/forum/viewtopic.php?t=589818) — Long-running discussion of the language from outside the project.
- [Cmajor Software on LinkedIn](https://www.linkedin.com/company/cmajor-software-ltd/) — Release and event announcements.

## Related Projects

- [SOUL](https://github.com/soul-lang/SOUL) — The earlier language from the same team, which Cmajor supersedes. Useful background reading; not a basis for new work.
- [JUCE](https://github.com/juce-framework/JUCE) — The C++ framework Cmajor exports plugin projects to.
- [CHOC](https://github.com/Tracktion/choc) — Julian Storer's header-only C++ utility collection, used throughout the Cmajor codebase.
- [Faust](https://faust.grame.fr) — The other major DSP language targeting many backends, and the closest point of comparison.
- [CLAP](https://cleveraudio.org) — The open plugin format Cmajor exports to natively.
- [Awesome Audio DSP](https://github.com/BillyDM/Awesome-Audio-DSP) — Broader list of DSP learning resources and libraries.
- [Awesome Music DSP](https://github.com/olilarkin/awesome-musicdsp) — Long-standing catalogue of audio DSP libraries and tools.

## Contributing

Contributions are welcome. Please read the [contribution guidelines](contributing.md) first — in short: one item per pull request, a one-line description of *why* the resource is worth someone's time, and no self-promotion of empty repositories.
