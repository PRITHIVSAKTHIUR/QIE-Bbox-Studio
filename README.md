# QIE-Bbox-Studio

QIE-Bbox-Studio (Qwen Image Edit Bounding Box Studio) is an advanced AI-powered image editing interface built on top of the Qwen2.5-VL and Qwen-Image-Edit models. This application allows users to manipulate images with extreme precision by defining bounding boxes and providing natural language prompts. 

By leveraging the capabilities of `Qwen/Qwen-Image-Edit-2511` and specialized adapter models, QIE-Bbox-Studio seamlessly executes targeted editing tasks like object removal, design addition, and object moving.

## Key Features

- **Interactive Bounding Box (Bbox) Editing:** Directly draw bounding boxes on images to define the exact area of effect for your edits.
- **Multiple Editing Modes:** The studio comes equipped with specialized adapters tailored for distinct image manipulation tasks:
  - **Object-Remover:** Intelligently removes highlighted objects from the scene and seamlessly fills the background. (Adapter: `prithivMLmods/QIE-2511-Object-Remover-Bbox-v3`)
  - **Design-Adder:** Adds intricate design patterns or new elements strictly inside the defined bounding box area. (Adapter: `prithivMLmods/QIE-2511-Outfit-Design-Layout`)
  - **Object-Mover:** Moves an object highlighted in a source bounding box to a destination indicated by another bounding box. (Adapter: `prithivMLmods/QIE-2511-Object-Mover-Bbox`)
- **State-of-the-Art Architecture:** Utilizes `QwenImageEditPlusPipeline` alongside Flash Attention 3 (`QwenDoubleStreamAttnProcessorFA3`) for accelerated, high-fidelity image processing.
- **User-Friendly Interface:** Built with Gradio to ensure an intuitive and accessible web-based user experience.

## Technology Stack

- **Core Models:** Qwen-Image-Edit-2511, Qwen-Image-Edit-Rapid-AIO-V19 (Transformer)
- **Frameworks:** PyTorch (2.8.0+), Hugging Face Diffusers, Transformers, PEFT, Accelerate
- **User Interface:** Gradio
- **Hardware Acceleration:** CUDA (Torch bfloat16), Flash Attention 3

## Installation and Setup

### Prerequisites

- Python 3.10 or higher
- A CUDA-compatible GPU with sufficient VRAM (recommended for optimal performance)

### Installation Steps

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/PRITHIVSAKTHIUR/QIE-Bbox-Studio.git
   cd QIE-Bbox-Studio
   ```

2. **Install Dependencies:**
   Install the necessary packages via the requirements files provided.
   ```bash
   pip install -r pre-requirements.txt
   pip install -r requirements.txt
   ```

## Usage

Start the web interface locally by running the main application script:

```bash
python app.py
```

Once the application is running, a local URL (e.g., `http://127.0.0.1:7860`) will be provided in your terminal. Open this URL in your web browser to access the studio.

### How to Edit an Image

1. **Upload an Image:** Use the interface to upload your source image or select one from the provided examples.
2. **Select an Editing Mode:** Choose from Object-Remover, Design-Adder, or Object-Mover.
3. **Draw Bounding Boxes:** Use the interactive canvas to draw red bounding boxes around your targets.
4. **Enter a Prompt:** Provide a text prompt describing the desired edit (e.g., "Remove the red highlighted object from the scene").
5. **Generate:** Click the generation button to process the image. The model will interpret the bounding boxes and apply the edit accordingly.

## Project Structure

- `app.py`: The main Gradio application script containing the UI logic and model inference setup.
- `qwenimage/`: Contains core pipeline definitions and custom attention processors (e.g., `pipeline_qwenimage_edit_plus.py`, `transformer_qwenimage.py`).
- `examples/`: Sample images provided for quick testing.
- `requirements.txt`: Python package dependencies.

## License

This project is licensed under the Apache License 2.0. Please refer to the `LICENSE.txt` file for more information.
