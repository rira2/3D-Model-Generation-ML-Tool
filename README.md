# 3D-Model-Generation-ML-Tool

## Project Overview

This project demonstrates the generation of 3D objects from text prompts using OpenAI's cutting-edge **Shap-E** text-to-3D diffusion model. It allows users to describe a 3D object in natural language, and the model then generates a latent 3D representation which is subsequently decoded into a usable 3D mesh. The primary goal is to showcase capabilities in applying advanced NLP and diffusion models for game-relevant asset generation.

## What the Project Does

* Accepts a text prompt describing a 3D object (e.g., `"a cute red mushroom with white spots"`).
* Uses OpenAI's **Shap-E** text-to-3D diffusion model to generate a latent 3D representation.
* Decodes the latent into a 3D mesh.
* Saves the output as:
    * `.obj` (geometry)
    * `.glb` (standard for game engines)
    * `.gif` (preview render from multiple camera angles)
* All outputs are saved to a folder called `generated_3d_models/`.

---

## How to Run

### Option 1: Google Colab (Recommended)

The easiest way to run this project is by using the provided Google Colab notebook, which handles environment setup and GPU access.

**[Open in Colab](https://colab.research.google.com/drive/1ccddWYutaKQQF2Ggj7aBOAV79mhHIcLD#scrollTo=_PG2lUXi-389)** 

1.  Open the notebook in Google Colab.
2.  Run all cells in order (usually `Runtime` > `Run all`).
3.  When prompted, enter a description for your 3D object (e.g., `"a cartoon-style robot"` or `"a red mushroom"`).
4.  The generated `.obj`, `.glb`, and `.gif` files will be saved to the `generated_3d_models/` directory within your Colab environment and can be downloaded from there.

### Option 2: Local (Optional)

Running locally requires a capable machine with Python and potentially a GPU for faster generation.

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/shap-e-3d-generator.git](https://github.com/YOUR_USERNAME/shap-e-3d-generator.git) # Replace YOUR_USERNAME
    cd shap-e-3d-generator # Navigate into your project directory
    ```
2.  **Install dependencies:**
    *(Ensure you have a Python environment set up, ideally a virtual environment)*
    ```bash
    pip install -r requirements.txt
    ```
3.  **Run the generation script:**
    *(Instructions for running the local script would go here, e.g., `python generate_3d_model.py` and how to provide a prompt)*

---

## Sample Outputs

**Prompt:** `"a cute red mushroom with white spots"`

* **Output `.obj`**: `generated_model_0.obj`(Renamed in repository as per the prompt for easy understanding , but real files are saved in this manner only)
* **Output `.glb`**: `generated_model_0.glb`(Renamed in repository as per the prompt for easy understanding , but real files are saved in this manner only)
    
You can open `.obj` or `.glb` files in 3D viewing tools like **Blender**, **Windows 3D Viewer**, or web-based viewers like:
* [https://gltf-viewer.donmccurdy.com](https://gltf-viewer.donmccurdy.com/)
* [https://3dviewer.net/](https://3dviewer.net/)

---

## Colab Demo and Video Walkthrough

A walkthrough demo of the project (showcasing setup, generation, and output) is available here:

**Demo Video:** [https://drive.google.com/drive/folders/1IsUXe5VJOSdFvxrYPy_Jv-C4Eln13TPr?usp=share_link] 
---

## API (Attempted Integration)

An attempt was made to integrate a web API using **FastAPI** with the project, aiming to enable 3D model generation via HTTP endpoints.

Unfortunately, during local development, **persistent tunneling issues were encountered**:

* Various internal tunneling services (e.g., `ngrok`, `localtunnel`) were tried, as well as external approaches.
* Tunnels often failed to establish properly, or they lost connection unpredictably, particularly during the resource-intensive model generation process. This prevented stable exposure of the API locally.

The attempted implementation can be seen in `app/main.py` *(Note: Adjust this path if your API file is different, e.g., `app.py`)*. With more development time or a robust deployment service, this API could be fully functional and production-ready.

---

## What I'd Improve with More Time/Resources

1.  **Robust Web API Deployment**: Fully deploy the 3D generation as a stable web API using **FastAPI** and host it on dedicated platforms like **Railway**, **Render**, or **Hugging Face Spaces**. This would resolve the local tunneling issues and provide a reliable, accessible service.
2.  **Interactive Web-based 3D Viewer**: Integrate a client-side web-based 3D viewer (e.g., using libraries like `three.js` or `Babylon.js`) directly into the web interface. This would allow users to interactively preview generated models in-browser without needing external software.
3.  **Batch Prompt Input**: Implement functionality to allow users to input multiple prompts at once, enabling the generation of a batch of 3D assets more efficiently.
4.  **Improved `.glb` Export Compatibility**: Further optimize the `.glb` export pipeline to ensure maximum compatibility and efficiency for direct import into popular game engines like **Unity** or **Unreal Engine**.
5.  **Advanced Model Control**: Explore adding parameters to the API/interface that allow users to control aspects of the 3D generation beyond just the prompt (e.g., resolution, style variations, number of faces, etc.).
6.  **Explore Other 3D Diffusion Models**: Investigate and experiment with other emerging text-to-3D diffusion models (e.g., MVDream, Point-E, Splatting-based methods) for comparison or alternative generation capabilities.
