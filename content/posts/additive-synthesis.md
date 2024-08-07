---
title: Additive Synthesis
---


Additive synthesis, a powerful technique for sound generation, forms the backbone of `raudio`— an innovative synthesizer built with Rust.


`raudio` pushes the boundaries of traditional physical modeling by introducing **Druidic Synthesis**, a method that ventures beyond natural sound reproduction into the realm of the fantastical. Designed with precision tuning in mind, it supports Just Intonation and the novel Monic Playbooks format.

This project represents a deep dive into digital signal processing (DSP), combining cutting-edge technology with creative exploration.

## Why would anybody build a digital synthesizer from scratch?

My motive to research and develop raudio is twofold:

1. I needed a tool that was designed for Just Intonation and also able to accept Monic Playbooks as input.
2. It was the largest DSP project for me yet, which offered a lot to learn.

## Druidic Synthesis

Druidic Synthesis offers generation-time dynamic modulation, allowing a sound to morph from a classic square wave into an unearthly synth. It provides three primary methods of modulation:

1. Conventional ADSR envelopes (for each of amplitude, frequency, phase offset).
2. Conventional "guitar effects" (a list of constant or time-varying modulators for each of amplitude, frequency, phase).
3. Novel "modbox" effect (a list of per-sample, per-multiplier (harmonic) modulators for each of amplitude, frequency, phase, and cps (time)).

The third point is the driving reason why additive synthesis is the choice synthesis model.

## What is Just Intonation?

*Just Intonation* is the most correct tuning system.

Unfortunately, our world has been plagued with 12-tone Equal Temperament music for centuries as our ability to reproduce exact ratios was constrained by physical hardware (like an organ, harp, or guitar). While 12-ET is convenient and sounds good enough, it's literally an "average" tuning system.

Other instruments, like the human voice, stringed instruments, and trombones, don’t have to make this compromise because they have continuous access to the Frequency Domain. That means when you listen to a string quartet, a barbershop quartet, a choir, or a mass of trombone players, you're listening to an ensemble capable of providing absolutely perfect tuning!

You can sense a different quality to the music, as perfect tuning reveals more **sympathetic resonance** in the room it is performed in. This additional resonance gives music rendered with Just Intonation a distinct clarity and pleasant quality. While most lay ears may not be able to distinguish why the sound is different, they will be able to appreciate the additional beauty that comes with Just Intonation.

## What is a Monic Playbook?

I am the author of Monic Theory, a generic model for music composition. Monic Theory is a superset of MIDI (aka 12-ET), which means it can be converted to this lower form of musical representation.

Using the Monic representation for tones offers more information about the context and direction of tones. It also retains information about how to accurately create Just Intonation renditions of any melody.

A Monic Playbook is a kind of musical score that maintains this pure representation of tone.

As this is a new format for musical representation, there are no existing synthesizers that are capable of rendering Monic Playbooks.

I had developed an interpreter in SuperCollider to read Monic scores; however, this did not prove to be a sustainable (maintainable) solution as SuperCollider is a dynamically typed scripting language.

## Why Rust?

The best way to learn a new language is to build something with it!

The cool kids were talking about Rust, and I saw how it offers many safety features that were lacking in SuperCollider out of the box. It's been a pattern that I learn 1-2 languages every year, and in early 2024, it was Rust.

Rust also offers excellent performance benefits out of the box! For example, the language's built-in sine method has proven to be faster than a sine-cache method I implemented, as well as an interpolation method I implemented. This is very important for an application that makes O(n) sine calls `SAMPLE_RATE` times per second.

You can see the source code for raudio [here](https://github.com/ckmahoney/raudio).

## Engagement

If you are knowledgeable about DSP, consider opening a PR or creating GitHub issues. If you're software-savvy but not familiar with DSP, clone the repo and run the demos to render some audio. For all other readers, feel free to reach out with questions about Druidic Synthesis.
