# I3N
This package contains the accompanying code for the following paper:

## We illustrate the training details as follows:
## Installation
1. Clone this repository
2. cd I3N
3. Make virtual environment with Python 3.8 (e.g., conda create -n change python=3.8)
4. Install requirements (pip install -r requirements.txt)
5. [Clone COCO caption eval tools with Python 3.](https://gitee.com/tuyunbin/coco-caption_python3.git)

## Data
1. Download data from here: [google drive link](https://drive.google.com/file/d/1HJ3gWjaUJykEckyb2M0MB4HnrJSihjVe/view?usp=sharing)
```
python google_drive.py 1HJ3gWjaUJykEckyb2M0MB4HnrJSihjVe clevr_change.tar.gz
tar -xzvf clevr_change.tar.gz
```

* Extract visual features using ImageNet pretrained ResNet-101:
```
# processing default images
python scripts/extract_features.py --input_image_dir ./data/images --output_dir ./data/features --batch_size 128

# processing semantically changes images
python scripts/extract_features.py --input_image_dir ./data/sc_images --output_dir ./data/sc_features --batch_size 128

# processing distractor images
python scripts/extract_features.py --input_image_dir ./data/nsc_images --output_dir ./data/nsc_features --batch_size 128
```

* Build vocab and label files using caption annotations:
```
python scripts/preprocess_captions_pos.py --input_captions_json ./data/change_captions.json --input_neg_captions_json ./data/no_change_captions.json --input_image_dir ./data/images --input_pos ./data/pos_token.pkl --split_json ./data/splits.json --output_vocab_json ./data/vocab.json --output_h5 ./data/labels.h5
```

