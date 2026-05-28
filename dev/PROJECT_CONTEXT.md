# finvolution-wedunthink — Project Context

_Primary context hub for all Agent J agents working in this repo._
_Read this before starting any task. Update it when architecture or state changes materially._

## Project Overview
This project is for an algorithm-focused data science competition on turn-taking prediction in multi-dialect Chinese conversations. The goal is to predict speech events in the next 2 seconds (25 chunks of 80ms) based on up to 30 seconds of dual-channel conversation audio and associated text information. The possible labels are Continuation (C), Turn Change (T), Backchannel (BC), Interruption (I), and Silence (NA).

## Tech Stack
- **Language:** Python (assumed based on `.npy` and `.json` data files).
- **Audio Processing:** Dual-channel stereo conversation audio (`.wav`).
- **NLP:** Text information corresponding to the audio (`.json`).
- **Constraints:** Total model size must not exceed 8 billion parameters.

## Current State
- Repository structure initialized with Agent J guidelines.
- Competition rules and task definitions provided.
- **No implementation code, data loaders, or models are currently present.**

## Architecture
- **Data Input:** Stereo audio (`.wav`), text metadata (`.json`), and temporal labels (`.npy`).
- **Data Segmentation:** 30s context + 2s prediction window (80ms chunks).
- **Labels:** 0=C, 1=T, 2=BC, 3=I, 4=NA.
- **Pipeline:** (Planned) Audio/text feature extraction -> Contextual modeling -> Temporal label prediction.

## Active Constraints
- **Model Size:** Maximum 8B parameters (including pre-trained models).
- **Originality:** Must be original work; plagiarism is strictly prohibited.
- **Data Usage:** Only publicly available datasets listed on the competition website or pre-notified models/datasets are allowed.
- **Execution:** No exploitation of rule ambiguities, unauthorized crawlers, or database/vector-library collision methods.

## Open Questions
- What are the specific evaluation metrics (e.g., F1-macro, accuracy)?
- Which deep learning framework is preferred (PyTorch, TensorFlow, Jax)?
- Where is the official data hosted, and how will it be integrated into the local environment?
