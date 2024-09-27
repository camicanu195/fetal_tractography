
# 3D Tractography Visualization and Fetal Brain Tractography Pipeline

## Overview
This repository contains two tutorials:

1. **Fetal Brain Tractography Pipeline**: This pipeline is for processing fetal brain data. It includes steps for processing tissue and parcellation segmentations, generating diffusion-based tractography, and extracting specific tracts.
   
2. **3D Tractography Visualization**: This tutorial demonstrates how to visualize tractography in 3D using diffusion imaging data. It explains how to render tractography streamlines, brain structures, and anatomical slices in a 3D scene.

---

## Dependencies

### General Dependencies (for both tutorials):
- **Python 3.x**
- **Jupyter Notebook**

### Python Libraries:
- **dipy**
- **nibabel**
- **ants**
- **SimpleITK**
- **pandas**
- **numpy**
- **scipy** 
- **matplotlib**
- **skimage**

### Fetal Brain Tractography Specific:
   - **MRTrix**: https://www.mrtrix.org/
   - **tract_querier**: https://tract-querier.readthedocs.io/en/latest/

---

## How to Run

### 1. **Fetal Brain Tractography Pipeline**:
   - Follow the steps in `Tutorial.ipynb` to process fetal brain data.
   - Execute the pipeline in sequential order to perform tensor-to-ODF conversion, tractography generation, and tract extraction.

### 2. **3D Tractography Visualization**:
   - Follow the instructions in the notebook `tract_visulization_tutorial.ipynb`.
   - Run the cells step-by-step to visualize 3D tractography using the loaded diffusion imaging data and anatomical structures.


---

## Function Overview

### `tract_viz_utils.py`

- **`display_scene`**: Displays a 3D scene using a temporary image file.
- **`hex_to_rgb`**: Converts a hex color code to its RGB equivalent.
- **`adjust_window_level`**: Adjust window level of an image for better visualization.
- **`add_tract_to_scene`**: Adds tractography streamlines from a `.tck` file to the 3D scene.
- **`add_image_slice`**: Adds a slice of the brain image to the scene at a specified axis and slice index.
- **`add_brain`**: Adds a 3D brain model to the scene using.
- **`create_obj_file`**: Converts a segmentation file into an `.obj` format for 3D rendering.
- **`obj_to_nv`**: Converts a 3D object file (`.obj`) into a Neuroimaging Visualization format.

### `utils.py`

- **`dilate_image(image, radius)`**: Binary dilation of an image using SimpleITK.
- **`add_spine_label(image, voxel_size, brainstem_label=94, spine_label=160)`**: Converts part of the brainstem to a spine label for tractography.
- **`ws_dialte`**: dilates labels using watershed algorithm.

### `adjust_parcellation.py`

- **`adjust_parcellation`**: Adjusts parcellation segmentation to align white matter regions with the tissue segmentation.

### `extract_labels.py`

- **`extract_individual_labels`**: Extracts individual labels from a NIfTI segmentation and saves them as separate NIfTI files.

### `fivett_gen.py`

- **`fivett_segmentation`**: Creates a 5-tissue-type segmentation from a T2-weighted image.

### `get_max_min_streamline.py`

- **`calculate_streamline_lengths`**: Calculates the minimum and maximum lengths for optimal tractography.

### `tensor2odf.py`

- **`compute_fod_sh`**: Converts diffusion tensor data into fiber orientation distribution (FOD) using spherical harmonics.

### `create_ctx_wm.py`

- **`parcellation_ctx_wm`**: Creates the cortical white matter interface for tractography.
