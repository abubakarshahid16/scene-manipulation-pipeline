# Scene Manipulation Pipeline

A modular computer-vision pipeline for editing scenes from natural-language instructions.

The system is designed around two core capabilities:

- object-level relocation
- lighting or relighting transformation

It combines instruction parsing, detection, segmentation, inpainting, composition, and evaluation into a single research-style workflow.

## Problem this project solves

Image editing systems often require direct manual masking or highly specialized tooling. A text-guided scene-editing pipeline aims to reduce that friction by allowing users to describe edits in natural language instead of performing every transformation by hand.

This project explores how to turn prompts such as:

- move the car to the left
- make the lighting warmer
- create a more dramatic scene

into structured visual transformations.

## Pipeline overview

The workflow is organized as:

1. instruction parsing
2. object identification and segmentation
3. object relocation or lighting transformation
4. scene repair and composition
5. output evaluation

## Example outputs

| Original | Comparison |
| --- | --- |
| ![Original scene](original.png) | ![Comparison output](comparison.png) |

| Relocation | Lighting Change |
| --- | --- |
| ![Car moved](car_moved.png) | ![Warm lighting](warm_lighting.png) |

## Repository contents

- `pipeline.py`: main orchestration logic
- `instruction_parser.py`: text instruction parsing
- `object_detector.py`, `segment_anything.py`, `mask_processor.py`: localization and segmentation logic
- `object_relocator.py`, `compositor.py`, `inpainting_model.py`: edit and composition components
- `evaluation.py`: evaluation utilities
- `demo.py`, `simple_demo.py`, `example_usage.py`: runnable examples
- output images such as `comparison.png`, `car_moved.png`, and lighting variants

## Why this project matters

- It demonstrates multimodal pipeline design.
- It combines language understanding with visual transformation.
- It is stronger than a single-model demo because the workflow is modular.
- It provides visible before/after evidence of the system behavior.

## Run locally

```bash
pip install -r requirements.txt
python demo.py
```

If the environment requires model assets first:

```bash
python download_models.py
```

## Industrial positioning

A production-grade scene-editing system would usually add:

- more robust instruction grounding
- stronger failure handling when objects are ambiguous
- faster inference and model packaging
- richer support for multiple object types and edit intents
- evaluation datasets and user quality metrics

This makes the repository best positioned as a **research and prototyping pipeline for text-guided scene editing**.
