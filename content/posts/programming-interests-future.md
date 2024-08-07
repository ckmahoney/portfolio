---
title: Programming Interests (todo)
---

These are some topics that are fascinating but cost too much time for me to do them right now. They are mentioned here because I believe these items are important enough that I'll get to them sooner than later.

## SIMD Optimizations

Single Instruction, Multiple Data (SIMD) is a powerful optimization technique for DSP. Since my additive synthesizer, raudio, is already vectorized, the next logical step is to leverage SIMD to perform operations on multiple data points simultaneously. This would allow the processor to execute additions and multiplications across vectors of data in parallel, significantly improving performance.

While the potential runtime savings are substantial, developing this feature is time-consuming. Since I am new to SIMD programming, I need to learn how to implement it effectively in Rust on Debian, as implementations vary by language and operating system. As this is an optimization, I'm adhering to the adage, "Build it first, then optimize later."

## Binary Encoders & Decoders

Currently, my Monic Playbooks are stored as either plain JSON files (eeek!) or tokenized data in a SQL database (also eeek!).

This has been working for a couple of years and makes reading the files pretty straightforward. However, JSON has some limitations:

- A UTF-8 representation of data is much more expensive in terms of disk space than a binary representation.
- Parsing UTF-8 data requires more compute than parsing binary data.
- Full-text search is an entire class of problems that can be avoided.

Or, in other words, the benefits of a binary representation of Monic Playbooks include:

- Less overall disk usage.
- More universal application acceptance (assuming a decoder is created for the application or language).
- Faster searches using bitmasks.

## Audio File Format Specifications

Currently, I use minimum working knowledge of the WAV format to render audio files. Additional free codecs include:

- FLAC
- OGG Vorbis
- Opus
- WebM

As always, we want the best tool for the job. I'd like to better understand the details on when to use each of these and would like to support rendering and transcoding targets for them.
