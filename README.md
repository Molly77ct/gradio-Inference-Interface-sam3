# SAM3 Gradio Inference Interface

A Gradio-based web interface for performing image and video segmentation using Meta's SAM 3 (Segment Anything with Concepts) model.

This project provides an easy-to-use graphical interface that allows users to run SAM 3 inference on images and videos without interacting directly with Python scripts. The application supports text-prompt segmentation and video object tracking through a browser-based interface powered by Gradio.

---

## Features

* Image segmentation using text prompts
* Video segmentation and object tracking
* Interactive web interface built with Gradio
* Integration with Meta's SAM 3 model
* Automatic video frame extraction using FFmpeg
* Hugging Face model checkpoint support
* GPU acceleration with CUDA

---

## Technologies Used

* Python 3.12
* PyTorch 2.7
* CUDA 12.6+
* Gradio
* SAM 3
* Hugging Face Hub
* FFmpeg
* UV (Ultraviolet Package Manager)

---

## Model Access

SAM 3 checkpoints are hosted on Hugging Face and require approval before download.

Request access at:

https://huggingface.co/facebook/sam3

Once access is granted, authenticate using:

```bash
hf auth login
```

You will need a Hugging Face access token associated with an approved account.

---

## Prerequisites

Before installing the project, ensure your system meets the following requirements:

* Python 3.12 or higher
* PyTorch 2.7 or higher
* CUDA-compatible GPU with CUDA 12.6 or higher

---

## Installation

### 1. Create a Conda Environment

```bash
conda create -n sam3 python=3.12
conda deactivate
conda activate sam3
```

### 2. Install PyTorch

```bash
pip install torch==2.7.0 torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126
```

### 3. Clone and Install SAM 3

```bash
git clone https://github.com/facebookresearch/sam3.git

cd sam3

pip install -e .
```

### 4. Install Additional Dependencies

For notebooks:

```bash
pip install -e ".[notebooks]"
```

For development and training:

```bash
pip install -e ".[train,dev]"
```

### 5. Install Hugging Face Hub

```bash
pip install huggingface_hub
```

### 6. Install UV

```bash
pip install uv
```

Or follow the official installation guide:

https://docs.astral.sh/uv/

### 7. Install FFmpeg

FFmpeg is required to extract video frames before processing.

Windows:

```bash
winget install FFmpeg
```

Verify installation:

```bash
ffmpeg -version
```

---

## Downloading SAM 3 Checkpoints

After obtaining Hugging Face access:

```bash
hf auth login
```

Then download the required SAM 3 checkpoint.

---

## Running the Application

Launch the Gradio interface:

```bash
python app.py
```

The application will start a local web server and provide a URL similar to:

```text
http://127.0.0.1:7860
```

Open the URL in your browser to begin inference.

---

## Image Inference Workflow

1. Upload an image.
2. Enter a text prompt.
3. Run inference.
4. Visualize the segmented masks and detections.

Example prompts:

```text
person
vehicle
tree
building
road
```

---

## Video Inference Workflow

1. Upload an MP4 video.
2. FFmpeg extracts frames automatically.
3. Enter a text prompt.
4. SAM 3 performs segmentation and tracking.
5. Results are visualized through the Gradio interface.

Example prompts:

```text
person
car
truck
vegetation
animal
```

---

## Project Structure

```text
SAM3-Gradio/
│
├── assets/                 # Images, GIFs and project resources
├── examples/               # Example notebooks and demos
├── models/                 # Model configurations and checkpoints
├── sam3/                   # Core SAM 3 implementation
├── scripts/                # Utility and evaluation scripts
│
├── gradio.py               # Main Gradio interface
├── video_chunk_worker.py   # Video processing and frame chunking
│
├── README.md
├── README_TRAIN.md
├── pyproject.toml
├── uv.lock
├── MANIFEST.in
│
├── LICENSE
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
└── .gitignore
```

---

## Applications

This project can be used for:

* Object segmentation
* Video object tracking
* Drone-based monitoring
* Environmental monitoring
* Agricultural analysis
* Vegetation segmentation
* Smart surveillance
* Research in computer vision

---

## Acknowledgments

This project uses the official SAM 3 model developed by Meta AI and distributed through Hugging Face.

* SAM 3: https://github.com/facebookresearch/sam3
* Hugging Face: https://huggingface.co/facebook/sam3
* Gradio: https://www.gradio.app/

---

## License

This project follows the license terms of the original SAM 3 repository and associated model checkpoints.
