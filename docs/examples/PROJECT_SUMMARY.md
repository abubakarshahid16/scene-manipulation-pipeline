# Scene Manipulation Pipeline - Project Summary

## 🎯 Project Overview

This project implements a comprehensive **Scene Manipulation Pipeline** that enables text-controlled object relighting and relocation in images. The system takes natural language instructions and performs sophisticated scene modifications using state-of-the-art computer vision and AI techniques.

## 🏗️ Architecture Overview

The pipeline consists of five main components:

### 1. Text Instruction Parsing (`src/text_parser/`)
- **InstructionParser**: Converts natural language to structured actions
- **ActionExtractor**: Validates and processes parsed actions
- Supports complex instructions like "Move the red car to the left and add sunset lighting"

### 2. Object Identification & Segmentation (`src/segmentation/`)
- **ObjectDetector**: Uses DETR for object detection
- **SAMSegmenter**: Uses Segment Anything Model for precise segmentation
- **MaskProcessor**: Post-processes and refines segmentation masks

### 3. Object Relocation (`src/relocation/`)
- **ObjectRelocator**: Main relocation orchestrator
- **SpatialPlanner**: Plans optimal object placement
- **Compositor**: Seamlessly composites objects into new locations

### 4. Relighting (`src/relighting/`)
- **LightingTransformer**: Applies various lighting effects
- Supports sunset, golden hour, dramatic, warm, cool, and other lighting types
- Local and global lighting transformations

### 5. Diffusion Models (`src/diffusion/`)
- **InpaintingModel**: Uses Stable Diffusion for object removal and scene completion
- Handles seamless background filling after object relocation

## 🚀 Key Features

### Natural Language Understanding
- Parse complex instructions with multiple actions
- Extract object references, spatial directions, and lighting preferences
- Validate and prioritize actions

### Advanced Object Manipulation
- Precise object detection using DETR
- High-quality segmentation using SAM
- Seamless object relocation with inpainting
- Spatial planning for optimal placement

### Sophisticated Lighting Control
- Multiple lighting presets (sunset, golden hour, dramatic, etc.)
- Local and global lighting transformations
- Lighting consistency and quality assessment

### Quality Assurance
- Comprehensive evaluation metrics (SSIM, PSNR, LPIPS)
- Performance monitoring and optimization
- Fallback mechanisms for robustness

## 📁 Project Structure

```
├── src/
│   ├── text_parser/          # Natural language processing
│   │   ├── instruction_parser.py
│   │   └── action_extractor.py
│   ├── segmentation/         # Object detection & segmentation
│   │   ├── object_detector.py
│   │   ├── segment_anything.py
│   │   └── mask_processor.py
│   ├── relocation/           # Object relocation logic
│   │   ├── object_relocator.py
│   │   ├── spatial_planner.py
│   │   └── compositor.py
│   ├── relighting/           # Lighting transformations
│   │   └── lighting_transformer.py
│   ├── diffusion/            # Diffusion model utilities
│   │   └── inpainting_model.py
│   ├── utils/                # Helper functions
│   │   ├── image_utils.py
│   │   ├── visualization.py
│   │   └── evaluation.py
│   └── pipeline.py           # Main pipeline orchestrator
├── scripts/
│   └── download_models.py    # Model download script
├── demo.py                   # Comprehensive demo
├── example_usage.py          # Usage examples
├── test_pipeline.py          # Unit tests
├── requirements.txt          # Dependencies
└── README.md                 # Project documentation
```

## 🛠️ Installation & Setup

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Download Models
```bash
python scripts/download_models.py
```

### 3. Test Installation
```bash
python test_pipeline.py
```

## 💡 Usage Examples

### Basic Usage
```python
from src.pipeline import SceneManipulationPipeline

# Initialize pipeline
pipeline = SceneManipulationPipeline()

# Process image with instruction
result = pipeline.process(
    image_path="path/to/image.jpg",
    instruction="Move the red car to the left and add sunset lighting"
)

# Save results
result.save_outputs("outputs/")
```

### Advanced Usage
```python
# Multiple instructions in sequence
instructions = [
    "Move the car to the center",
    "Add golden hour lighting",
    "Relocate the person to the background"
]

for instruction in instructions:
    result = pipeline.process(image_path, instruction)
    # Process result...
```

## 🎨 Supported Instructions

### Object Relocation
- "Move the car to the left"
- "Relocate the person to the center"
- "Move the tree to the background"

### Lighting Effects
- "Add sunset lighting to the entire scene"
- "Apply golden hour lighting to the car"
- "Add dramatic lighting to the person"

### Combined Operations
- "Move the car to the left and add sunset lighting"
- "Relocate the person to the center and apply golden hour lighting"

### Spatial References
- left, right, center, top, bottom
- foreground, background, front, back

### Lighting Types
- sunset, golden_hour, dramatic, soft, harsh
- warm, cool, natural, artificial

## 📊 Evaluation & Quality Metrics

The pipeline includes comprehensive evaluation capabilities:

- **SSIM (Structural Similarity Index)**: Measures image quality preservation
- **PSNR (Peak Signal-to-Noise Ratio)**: Quantifies image fidelity
- **LPIPS (Learned Perceptual Similarity)**: Perceptual quality assessment
- **Object Detection Accuracy**: Precision, recall, F1-score
- **Segmentation Quality**: IoU, Dice coefficient, pixel accuracy
- **Performance Metrics**: Execution time, bottlenecks, optimization recommendations

## 🔬 Technical Implementation

### Models Used
- **DETR (Detection Transformer)**: Object detection and localization
- **SAM (Segment Anything Model)**: Precise object segmentation
- **Stable Diffusion**: Inpainting and scene completion
- **spaCy**: Natural language processing

### Key Algorithms
- **Diffusion-based Inpainting**: Seamless object removal and background completion
- **Neural Relighting**: Learned lighting transformations
- **Spatial Planning**: Optimal object placement algorithms
- **Mask Processing**: Advanced segmentation refinement

### Performance Optimizations
- GPU acceleration where available
- Fallback mechanisms for robustness
- Batch processing capabilities
- Memory-efficient operations

## 🎯 Research Contributions

This project demonstrates several research-level contributions:

1. **Text-to-Scene Manipulation**: Novel pipeline for natural language controlled scene editing
2. **Multi-Modal Integration**: Seamless integration of vision and language models
3. **Quality-Aware Processing**: Comprehensive evaluation and quality assurance
4. **Robust Architecture**: Fallback mechanisms and error handling
5. **Extensible Design**: Modular architecture for easy extension

## 🚀 Future Enhancements

### Planned Features
- **Real-time Processing**: Optimize for interactive applications
- **Video Support**: Extend to video sequences
- **3D Scene Understanding**: Incorporate depth and 3D information
- **Advanced Lighting**: Physics-based lighting simulation
- **User Interface**: Web-based interface for easy interaction

### Research Directions
- **Few-shot Learning**: Adapt to new object types with minimal examples
- **Controllable Generation**: More precise control over object placement
- **Temporal Consistency**: Maintain consistency across video frames
- **Multi-object Interactions**: Handle complex object relationships

## 📚 References & Acknowledgments

### Research Papers
- [Segment Anything Model](https://arxiv.org/abs/2304.02643)
- [DETR: End-to-End Object Detection](https://arxiv.org/abs/2005.12872)
- [Stable Diffusion](https://arxiv.org/abs/2112.10752)
- [Neural Gaffer: Relighting Any Object via Diffusion](https://arxiv.org/abs/2303.12503)

### Libraries & Tools
- [PyTorch](https://pytorch.org/)
- [Transformers](https://huggingface.co/transformers/)
- [OpenCV](https://opencv.org/)
- [spaCy](https://spacy.io/)

## 🤝 Contributing

This is an open-ended research project. Contributions are welcome:

- **Code Improvements**: Bug fixes, performance optimizations
- **New Features**: Additional lighting types, object manipulation capabilities
- **Documentation**: Improved docs, tutorials, examples
- **Research**: Novel algorithms, evaluation metrics, use cases

## 📄 License

This project is for educational and research purposes. Please respect the licenses of the underlying models and libraries used.

---

**Project Status**: ✅ Complete Implementation  
**Last Updated**: June 2024  
**Version**: 1.0.0 