# Granite Fine-Tuning

This project is designed to fine-tune the ibm-granite/granite-vision-3.2-2b model using a subset of the google/wit dataset. Due to the lack of a GPU, the training process was limited.


## Installation

Run the following commands to install the required libraries:
```bash
pip install -q git+https://github.com/huggingface/transformers.git
pip install -U -q trl datasets bitsandbytes peft accelerate cairosvg
```

## Usage

The script is designed to fine-tune the Granite model using the google/wit dataset. To run it, execute:
```bash
python granit_fine_tune.py
```

Some key parameters used in the code:
- **USE_QLORA = True** → Enables quantization to optimize memory usage
- **USE_LORA = True** → Applies LoRA-based fine-tuning for efficient weight updates
- 
## Dataset

The fine-tuning process was conducted using a subset of the google/wit dataset. google/wit is a dataset based on image-text pairings and is commonly used for image captioning and multimodal model training. Due to hardware limitations, only a small portion of the dataset was used for training

## Technical Stack


- **Base Model: IBM Granite Vision 3.2-2B**
- **Dataset: Google Web Image Text (WIT) - Türkçe Alt Kümesi**
- **Fine-Tuning Method: Supervised Fine-Tuning (SFT) with LoRA**
- **Quantization: 4-bit Quantization (QLoRA)**
- **PEFT** (Parameter Efficient Fine-Tuning)


## Challenges

- **Limited Hardware:** Due to the absence of a GPU, lightweight fine-tuning methods such as QLoRA and LoRA were used.
- **Small Dataset:**  It was not possible to use the full dataset


