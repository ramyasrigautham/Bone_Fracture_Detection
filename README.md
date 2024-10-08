
# Bone Fracture Detection Using YOLO and Transfer Learning

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![YOLO](https://img.shields.io/badge/YOLO-v8-orange)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-green)
![License](https://img.shields.io/github/license/ramyasrigautham/Bone_Fracture_Detection)
![GitHub last commit](https://img.shields.io/github/last-commit/ramyasrigautham/Bone_Fracture_Detection)

## Project Overview

This project aims to develop an automated system for detecting bone fractures from X-ray images using the YOLO (You Only Look Once) object detection model and transfer learning techniques. The primary goal is to create a highly accurate model that can assist medical professionals in diagnosing bone fractures more efficiently.

## Features

- **YOLO Model**: Utilizes the YOLOv8 model for real-time object detection.
- **Transfer Learning**: Fine-tuned the YOLO model on a custom dataset of X-ray images.
- **High Accuracy**: Achieved high accuracy in detecting different types of bone fractures.
- **Easy Deployment**: Ready for deployment in medical applications or research projects.

## Table of Contents

- [Installation](#installation)
- [Dataset](#dataset)
- [Model Training](#model-training)
- [Usage](#usage)
- [Results](#results)
- [Running the Repository](#running-the-repository)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## Installation

### Prerequisites

- Python 3.8 or higher
- TensorFlow 2.x
- PyTorch
- Utralytics
- NumPy
- Pandas

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/ramyasrigautham/Bone_Fracture_Detection.git
   cd Bone_Fracture_Detection
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

## Dataset

The dataset used in this project consists of X-ray images with annotated bone fractures. https://www.kaggle.com/datasets/pkdarabi/bone-fracture-detection-computer-vision-project/data?select=BoneFractureYolo8

### Dataset Structure

```
Dataset/
├── images/
│   ├── image1.jpg
│   ├── image2.jpg
│   └── ...
└── labels/
    ├── image1.txt
    ├── image2.txt
    └── ...
```

## Model Training

To train the YOLO model on your dataset, use the following command:

```bash
results_medium = model_medium.train(data=DATA_YML,batch = 32,
                                epochs= 100,
                                #imgsz= 512,
                                # seed = 9418,
                                save_period = 10,
                                save= True,
                                optimizer = 'AdamW',
                                cos_lr = True,
                                lr0 = 0.001,
                                lrf = 0.00001,
                                cache = True,
                                weight_decay = 5e-4,
                                warmup_momentum = 0.6,
                                momentum = 0.9,
                                val=True,
                                patience= 0,
                                name = 'yolov8m',
                                profile= True
#                                 device = [0, 1])
                                )
```

This command will start the training process using the specified configuration file and dataset.

## Usage

After training the model, you can use it to detect fractures in new X-ray images. Use the following command to run the model on an image:

```bash
!yolo task=detect mode=predict model='/content/runs/detect/yolov8m2/weights/best.pt' conf=0.25 source='/content/drive/MyDrive/Colab Notebooks/Data/OriginalData/BoneFracture/test/images' save=True
```

The detected fractures will be highlighted in the output image.

## Running the Repository

To run the web application locally, follow these steps:

1. Clone the repository to your local machine.
2. Create a virtual environment for the project.
3. Install all the required dependencies.
4. Download the pre-trained weights for the models here. Make sure to add them in a `weights` folder in the project directory.
5. Run the following command in your terminal to run the app:
   ```bash
   streamlit run app.py
   ```

## Results

![Home Page](images/Yolo_homePage.jpg)

![Yolo Page](images/YOLO_PAGE.jpg)

The model achieved an accuracy of 70% on the test set. Below is an example of fracture detection:

![Example Detection](images/yolo_result.jpg)

Confusion Matrix:
![Matrix](images/yolo_ConfusionMatrix.jpg)

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add some feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Open a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- Special thanks to the [YOLO](https://github.com/ultralytics/yolov5) and [TensorFlow](https://www.tensorflow.org/) communities for their open-source contributions.
- Medical professionals who provided insights and annotated the dataset.

