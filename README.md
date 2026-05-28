# finvolution-wedunthink

Algorithm-focused data science challenge on **turn-taking prediction in multi-dialect Chinese conversations**.

## Overview

The goal of this competition is to predict speech events in the next 2-second window (25 chunks of 80ms) based on the past conversation context (up to 30 seconds of dual-channel audio and text).

### Task and Labels

For each prediction sample, the model predicts one of five possible event labels for each 80ms chunk:

| Label | Meaning |
| ----- | ------- |
| **C** | Continuation (current speaker keeps speaking) |
| **T** | Turn Change (other speaker takes over) |
| **BC** | Backchannel (short response without taking turn, e.g., "um") |
| **I** | Interruption (both speakers speak simultaneously) |
| **NA** | Silence (neither speaker speaks) |

## Dataset Structure

The training set consists of dual-channel telephone conversations:
- `audio/<conv_id>.wav`: Dual-channel audio.
- `text/<conv_id>.json`: Corresponding text information.
- `labels/<conv_id>.npy`: Temporal labels (0=C, 1=T, 2=BC, 3=I, 4=NA).

## Technical Constraints

- **Model Size:** Maximum 8 billion parameters.
- **Context Window:** Up to 30 seconds of history.
- **Prediction Window:** 2 seconds (25 chunks).

## Project Structure

- `dev/PROJECT_CONTEXT.md`: Detailed internal project state and architecture (Agent J context).
- `AGENTS.md`: Rules and guidelines for automated agents (Claude Code, Gemini, Codex).
- `.github/workflows/`: Automated implementation pipelines.

## Getting Started

*(Development is currently in the initialization phase. Data loading and baseline models are pending.)*
