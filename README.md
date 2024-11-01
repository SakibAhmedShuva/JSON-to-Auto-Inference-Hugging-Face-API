# JSON to Auto Inference Hugging Face API

## Overview

This Flask-based microservice provides Named Entity Recognition (NER) inference capabilities using Hugging Face's Transformers library. The service allows you to perform named entity extraction on text data through a RESTful API.

## Features

- 🤖 Supports pre-trained NER models from Hugging Face
- 📄 Handles JSON file and direct JSON data input
- 🔍 Intelligent entity span detection and combination
- 🚀 Easy model selection with automatic latest model detection
- 🌐 Supports various input formats

## Prerequisites

- Python 3.8+
- Flask
- Transformers
- PyTorch

## Installation

1. Clone the repository:
```bash
git clone https://github.com/SakibAhmedShuva/JSON-to-Auto-NER-Inference-Hugging-Face-API.git
cd JSON-to-Auto-NER-Inference-Hugging-Face-API
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

## Configuration

### Model Directory Structure
```
models/
│
└── [timestamp_or_version]/
    ├── config.json
    ├── pytorch_model.bin
    └── tokenizer files
```

## Usage

### Start the Service
```bash
python hf_inference.py
```

### Inference Endpoint

**Endpoint:** `/inference`
**Method:** POST

#### Request Formats

1. JSON File Upload
```python
files = {'file': open('input.json', 'rb')}
response = requests.post('http://localhost:5000/inference', files=files)
```

2. Direct JSON Data
```python
data = {
    "Objects": [
        {"Text": "John works at Google in Mountain View."}
    ]
}
response = requests.post('http://localhost:5000/inference', json=data)
```

#### Optional Parameters
- `model_path`: Specify a specific model version (defaults to latest model)

## Response Format

The service returns a list of annotation objects with:
- Entity spans
- Entity labels
- Confidence scores
- Unique identifiers

## Advanced Features

- Automatic consecutive entity combination
- Smart number span detection
- Flexible input parsing

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.
