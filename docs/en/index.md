<img src="../img/title.jpg" style="max-width:100%">



<a href="../en/index.md">English</a> | <a href="../ja/index.md">日本語</a> | <a href="../zh/index.md">繁体中文</a>

- <a href="index.md">Top</a>
- <a href="node.md">Node</a>
- <a href="workflow.md">Workflow</a>



# D2 Nodes ComfyUI

**D2 Nodes ComfyUI** is a collection of custom nodes created with the themes of "slightly convenient," "simple," and "maintaining versatility."

- Versatile XY Plot
- Workflow that automatically switches quality tags based on Checkpoint lineage
- Queue button with customizable batch count
- Various other "slightly convenient nodes"

## :exclamation: NOTICE

### Unnecessary Custom Nodes
If you have installed any of the following custom nodes previously, please remove them:

- [ComfyUI-d2-size-selector](https://github.com/da2el-ai/ComfyUI-d2-size-selector)
- [ComfyUI-d2-steps](https://github.com/da2el-ai/ComfyUI-d2-steps)
- [ComfyUI-d2-xyplot-utils](https://github.com/da2el-ai/ComfyUI-d2-xyplot-utils)

## :tomato: Nodes

- <a href="node.md#d2-ksampler--d2-ksampleradvanced">`D2 KSampler / D2 KSampler(Advanced)`</a>
  - KSampler that inputs and outputs prompts as STRING

### Text

- <a href="node.md#D2-Regex-Replace">`D2 Regex Replace`</a>
  - Text replacement node with multiple condition support
- <a href="node.md#D2-Regex-Switcher">`D2 Regex Switcher`</a>
  - Node that switches output text based on input text
  - Can also perform string concatenation
- <a href="node.md#D2-Multi-Output">`D2 Multi Output`</a>
  - Outputs SEED / STRING / INT / FLOAT as lists
- <a href="node.md#D2-List-To-String">`D2 List To String`</a>
  - Converts arrays to strings

### Loader

- <a href="node.md#D2-Checkpoint-Loader">`D2 Checkpoint Loader`</a>
  - Checkpoint Loader that outputs full model file paths
- <a href="node.md#D2-Controlnet-Loader">`D2 Controlnet Loader`</a>
  - Controlnet Loader that creates simple workflows when connected to D2 KSampler

### Image

- <a href="node.md#D2-Load-Image">`D2 Load Image`</a>
  - Load Image that can extract prompts from images
  - Compatible with images created in StableDiffusion webui A1111 and NovelAI
  - Includes a button to open mask editor
- <a href="node.md#D2-Load-Folder-Images">`D2 Load Folder Images`</a>
  - Loads all images from a folder
- <a href="node.md#D2-Folder-Image-Queue">`D2 Folder Image Queue`</a>
  - Sequentially outputs image paths from a folder
  - Automatically executes queue for all images
- <a href="node.md#D2-Grid-Image">`D2 Grid Image`</a>
  - Generates grid images
- <a href="node.md#D2-Image-Stack">`D2 Image Stack`</a>
  - Node for stacking multiple images to pass to D2 Grid Image
  - Outputs images directly
- <a href="node.md#D2-EmptyImage-Alpha">`D2 EmptyImage Alpha`</a>
  - Outputs EmptyImage with alpha channel (transparency)

### Size

- <a href="node.md#D2-Get-Image-Size">`D2 Get Image Size`</a>
  - Displays and retrieves image sizes
- <a href="node.md#D2-Size-Slector">`D2 Size Slector`</a>
  - Image size and Empty latent output node with preset selection
  - Can also get size from images
- <a href="node.md#D2-Image-Resize">`D2 Image Resize`</a>
  - Image resize with precision up to 3 decimal places
  - Options for rounding, floor, or ceiling
- <a href="node.md#D2-Resize-Calculator">`D2 Resize Calculator`</a>
  - Image size calculator that ensures results are multiples of 8
  - Options for rounding, floor, or ceiling

### XY Plot

- <a href="node.md#D2-XY-Plot">`D2 XY Plot`</a>
  - Versatile XY Plot node
  - Automatically executes required number of queues
- <a href="node.md#D2-XY-Grid-Image">`D2 XY Grid Image`</a>
  - Node for generating grid images
- <a href="node.md#D2-XY-Prompt-SR">`D2 XY Prompt SR`</a>
  - Searches and replaces text, returns as list. Placed before D2 XY Plot
- <a href="node.md#D2-XY-Prompt-SR2">`D2 XY Prompt SR2`</a>
  - Searches and replaces text, returns as list. Placed after D2 XY Plot
- <a href="node.md#D2-XY-Seed">`D2 XY Seed`</a>
  - Outputs list of SEEDs
- <a href="node.md#D2-XY-Checkpoint-List">`D2 XY Checkpoint List`</a>
  - Outputs list of Checkpoints
- <a href="node.md#D2-XY-Lora-List">`D2 XY Lora List`</a>
  - Outputs list of Loras
- <a href="node.md#D2-XY-Folder-Images">`D2 XY Folder Images`</a>
  - Outputs list of files in folder
- <a href="node.md#D2-XY-Annotation">`D2 XY Annotation`</a>
  - Creates header text for display in D2 Grid Image
- <a href="node.md#D2-XY-List-To-Plot">`D2 XY List To Plot`</a>
  - Converts arrays to D2 XY Plot lists

### Refiner
- <a href="node.md#D2-Refiner-Steps">`D2 Refiner Steps`</a>
  - Outputs steps for Refiner
- <a href="node.md#D2-Refiner-Steps-A1111">`D2 Refiner Steps A1111`</a>
  - Can specify denoise for Refiner in img2img
- <a href="node.md#D2-Refiner-Steps-Tester">`D2 Refiner Steps Tester`</a>
  - Node for checking steps

### Float Palet

- <a href="node.md#D2-Queue-Button">`D2 Queue Button`</a>
  - Button that generates specified number of images (Batch count)
- <a href="node.md#Prompt-convert-dialog">`Prompt convert dialog`</a>
  - Dialog for converting weights between NovelAI and StableDiffusion

## :blossom: Changelog

**2024.11.18**

- Added many nodes at once
- Added `D2 Controlnet Loader`, `D2 Get Image Size`, `D2 Grid Image`, `D2 Image Stack`, `D2 List To String`, `D2 Load Folder Images`
- Added XY Plot related nodes
- Added `D2 XY Annotation`, `D2 XY Checkpoint List`, `D2 XY Folder Images`, `D2 Grid Image`, `D2 XY List To Plot`, `D2 XY Lora List`, `D2 XY Plot`, `D2 XY Prompt SR`, `D2 XY Prompt SR2`, `D2 XY Seed`
- Existing nodes have also been modified, see commit history for details

**2024.11.02**

- `D2 Regex Switcher`: Added toggle for input text confirmation textarea

**2024.10.28**

- Added `Prompt convert`: Dialog for converting prompts between NovelAI and StableDiffusion
- `D2 Folder Image Queue`: Fixed issue where image generation count was inconsistent

**2024.10.26**

- Added new `D2 EmptyImage Alpha`
- Added new `D2 Image Resize`
- Added new `D2 Resize Calculator`

<summary><strong>2024.10.24</strong></summary>

- Added new `D2 Regex Replace`
- Added new `D2 Folder Image Queue`
- `D2 Load Image`: Added image path input
- `D2 KSampler(Advanced)`: Added Positive / Negative Conditioning to Input

<details>
  <summary><strong>2024.10.19</strong></summary>

- Added `D2 Queue Button`

</details>

<details>
  <summary><strong>2024.10.18</strong></summary>

- `D2 Size Selector`: Added ability to get size from images
- `D2 Size Selector`: Added option to choose between "rounding" and "floor" for resizing

</details>

<details>
<summary><strong>2024.10.14</strong></summary>

- `D2 Load Image`: Fixed error when loading images without Exif data (e.g., pasted from clipboard)

</details>

<details>
  <summary><strong>2024.10.11</strong></summary>

- `D2 Regex Switcher`: Added ability to specify separator character for string concatenation

</details>

<details>
  <summary><strong>2024.10.10</strong></summary>

- `D2 Load Image`: Added "Open Mask Editor" button

</details>

<details>
  <summary><strong>2024.10.08</strong></summary>
  
  - Added new `D2 Load Image`

</details>

<details>
  <summary><strong>2024.10.03</strong></summary>

- `D2 Regex Switcher`: Fixed bug where matches were being passed through without processing

</details>

<details>
  <summary><strong>2024.10.02</strong></summary>

- Created by integrating existing nodes

</details>