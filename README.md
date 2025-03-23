# RF-DETR with ONNX

This repository contains code to load an ONNX model—converted from RF-DETR—and perform inference, including drawing the results on images. It demonstrates how to convert a PyTorch model to ONNX format and run real-time inference with minimal dependencies.

RF-DETR is a transformer-based object detection architecture developed by Roboflow. For more details on the model, please refer to the impressive work by the Roboflow team [here](https://github.com/roboflow/rf-detr/tree/main).

## Official Repo vs ONNX Runtime Inference

On the left: Output from the official RF-DETR repository.  
On the right: Output using ONNX Runtime for inference.

<p align="center">
  <img src="illustration/exemple-official-repo.png", alt="Image 1" width="45%">
  <img src="illustration/exemple-onnx-inference.jpg", alt="Image 2" width="44.4%">
</p>

## Requirements

Ensure you have the following dependencies installed:
- onnxruntime
- Pillow
- numpy

Please note that the scripts have been tested with:
-  Python 3.11.11
-  onnxruntime 1.21.0
-  numpy 2.2.4
-  Pillow 11.1.0

First, clone the repository:

```bash
git clone <repository-url>
```

Then, install the required dependencies using pip:

```bash
pip install requirements.txt
```

# Download the Model

## Directly from Huggin-face

You can download the original model from Hugging Face using this link:

[Download Model from Hugging Face](https://huggingface.co/PierreMarieCurie/rf-detr-onnx/blob/main/rf-detr-base.onnx)

## Generate from the Original Repository

TO DO

# Inference Script Example

Below is an example showing how to perform inference on an image:

``` Python
from rf_detr import RTDETR_ONNX

# Get model and image
image_path = "https://media.roboflow.com/notebooks/examples/dog-2.jpeg"
model_path = "rf-detr-base.onnx"

# Initialize the model
model = RTDETR_ONNX(model_path)

# Run inference and get detections
_, labels, boxes = model.run_inference(image_path)

# Draw and display the detections
model.save_detections(image_path, boxes, labels, "saved_image.jpg")
```

# License

This repository is licensed under the MIT License.

Some portions of the code incorporate work released under the Apache License 2.0. These sections are clearly marked and include the required license and attribution information; please see the NOTICE file for further details regarding the Apache-licensed components.

In addition, RF-DETR itself is released under the Apache 2.0 license, and all aspects related to the model must comply with those terms.

# Acknowledgements
- Special thanks to the Roboflow team and everyone involved in the development of RF-DETR, particularly for sharing a state-of-the-art model under a permissive free software license.