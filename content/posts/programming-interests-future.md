---
title: Programming Interests (todo)
---

These are some topics that are fascinating but cost too much time for me to do them right now. They are mentioned here because I believe these items are important enough that I'll get to them sooner than later.


## SIMD Optimizations

Single Instruction, Multiple Data is the gold bar for DSP. Because my additive synthesizer, raudio, is already vectorized, the next logical step for optimizing is telling the complier that it can perform the additions and multiplications all at once (instead of checking which instruction set to use per-computation). 

While I understand the software runtime savings of this is large, the development of this feature is very time costly. I have not yet done any SIMD programming so that is a skill I need to learn how to implement (specifically in rust on debian; implementation varies per-language and operating system). Since this is an optimization, I'm following the old adage "Build it first, then optimize later."

## Binary Encoders & Decoders

Currently my Monic Playbooks are stored as either plain JSON files (eeek!) or tokenized data in a SQL database (also eeek!). 

This has been working for a couple years, and makes reading the files pretty straightforward. However, JSON has some limitations:

  - A UTF-8 representation of data is much more expensive in terms of disk space than a binary representation 
  - Parsing UTF-8 data requires more compute than parsing binary data 
  - Full text search is an entire class of problems that can be avoided


Or, in other words, benefits of a binary representation of Monic Playbooks include:

  - Less overall disk usage 
  - More universal application acceptance (assuming a decoder is created for the application or language)
  - Faster searches using bitmasks 

## Audio File Format Specifications

Currently, I use minimum working knowledge of the WAV format and use this to render audio files. Additional free codecs include:

  - FLAC
  - OGG Vorbis
  - Opus
  - WebM
  - MKV

As always, we want the best tool for the job. I'd like to better understand the details on when to use each of these, and would like to support render and transcoding targets for them.
