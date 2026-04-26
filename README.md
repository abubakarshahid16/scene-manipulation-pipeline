# Scene Manipulation Pipeline

A research-style computer-vision pipeline for scene manipulation using text instructions. The system targets object-level relocation and relighting by combining instruction parsing, segmentation, inpainting, and output composition.

## Overview

This project explores how natural-language instructions can be converted into visual scene edits such as:

- moving an object to a new location
- changing the scene lighting or object lighting
- generating composite outputs that reflect the requested manipulation

It is positioned as a pipeline-style CV project rather than a production application.

## Pipeline Components

1. text instruction parsing
2. object identification and segmentation
3. object relocation
4. relighting transformation
5. final image composition and evaluation

## Example Outputs

| Original | Comparison |
| --- | --- |
| ![Original scene](original.png) | ![Comparison output](comparison.png) |

| Relocation | Lighting Change |
| --- | --- |
| ![Car moved](car_moved.png) | ![Warm lighting](warm_lighting.png) |

## Repository Contents

- `pipeline.py`: main orchestration logic
- `instruction_parser.py`: natural-language instruction parsing
- `object_detector.py`, `segment_anything.py`, `mask_processor.py`: localization and segmentation logic
- `object_relocator.py`, `compositor.py`, `inpainting_model.py`: object edit and composition components
- `evaluation.py`: evaluation utilities
- `demo.py`, `simple_demo.py`, `example_usage.py`: runnable examples
- output images such as `comparison.png`, `car_moved.png`, and lighting variants

## Technical Themes

- text-guided image editing
- segmentation and object extraction
- inpainting-based scene repair
- relighting / illumination changes
- research-pipeline experimentation with modern CV models

## Why This Project Matters

This repository is a strong portfolio piece because it demonstrates:

- multimodal reasoning
- computer vision pipeline design
- research-oriented experimentation
- image editing through modular components
- visible before/after outputs

## Running the Project

Typical setup:

```bash
pip install -r requirements.txt
python demo.py
```

If required by the environment, download model assets first:

```bash
python download_models.py
```

## Current Repository Status

This project is best presented as a portfolio and experimentation repo. Its strength comes from the modular pipeline structure and example outputs rather than polished productization.

## Author

Abubakar Shahid  
GitHub: <https://github.com/abubakarshahid16>
