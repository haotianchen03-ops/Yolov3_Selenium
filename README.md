# Slide CAPTCHA Recognition with Deep Learning

This project uses a YOLOv3-based deep learning model to detect the gap position in slide CAPTCHA images. It is modified based on:[https://github.com/eriklindernoren/PyTorch-YOLOv3](https://github.com/eriklindernoren/PyTorch-YOLOv3)

With only a few hundred labeled gap images, you can train a high-accuracy detection model.
Example result:

![](data/captcha/result/captcha_435.png)
## Clone the Project

Run：

```
git clone https://github.com/Python3WebSpider/DeepLearningSlideCaptcha.git
```

## Data Preparation

Use the LabelImg tool to annotate your own dataset. Around 200+ labeled images are usually sufficient to achieve good performance.

LabelImg：[https://github.com/tzutalin/labelImg](https://github.com/tzutalin/labelImg)

Annotation Requirements：

* Draw a complete bounding box around the target gap region of the CAPTCHA.
* No need to annotate the original sliding block.
* The class name must be target.
* It is recommended to use LabelImg keyboard shortcuts to improve labeling efficiency.

## Environment Setup

It is recommended to use a GPU environment and a virtual Python environment.

Install dependencies:

```
pip3 install -r requirements.txt
```

## Download Pretrained Model

YOLOv3 requires pretrained weights to achieve good training performance.

Download pretrained weights:
```
bash prepare.sh
```

After downloading, the weight files will appear in the weights directory.
## Training

A labeled dataset is already provided under: data/captcha. You can directly use it for training.

If you want to train on your own dataset, please refer to: [https://github.com/eriklindernoren/PyTorch-YOLOv3#train-on-custom-dataset](https://github.com/eriklindernoren/PyTorch-YOLOv3#train-on-custom-dataset)。

Run the training script:

```
bash train.sh
```

## Testing

After training, .pth model files will be generated in the checkpoints directory.

You can use the trained model to perform prediction and generate detection results.

Run：

```
sh detect.sh
```

This script reads all images in: data/captcha/test, and outputs processed images into the same test folder.

Example Output:

```
Performing object detection:
        + Batch 0, Inference Time: 0:00:00.044223
        + Batch 1, Inference Time: 0:00:00.028566
        + Batch 2, Inference Time: 0:00:00.029764
        + Batch 3, Inference Time: 0:00:00.032430
        + Batch 4, Inference Time: 0:00:00.033373
        + Batch 5, Inference Time: 0:00:00.027861
        + Batch 6, Inference Time: 0:00:00.031444
        + Batch 7, Inference Time: 0:00:00.032110
        + Batch 8, Inference Time: 0:00:00.029131

Saving images:
(0) Image: 'data/captcha/test/captcha_4497.png'
        + Label: target, Conf: 0.99999
(1) Image: 'data/captcha/test/captcha_4498.png'
        + Label: target, Conf: 0.99999
(2) Image: 'data/captcha/test/captcha_4499.png'
        + Label: target, Conf: 0.99997
(3) Image: 'data/captcha/test/captcha_4500.png'
        + Label: target, Conf: 0.99999
(4) Image: 'data/captcha/test/captcha_4501.png'
        + Label: target, Conf: 0.99997
(5) Image: 'data/captcha/test/captcha_4502.png'
        + Label: target, Conf: 0.99999
(6) Image: 'data/captcha/test/captcha_4503.png'
        + Label: target, Conf: 0.99997
(7) Image: 'data/captcha/test/captcha_4504.png'
        + Label: target, Conf: 0.99998
(8) Image: 'data/captcha/test/captcha_4505.png'
        + Label: target, Conf: 0.99998
```

Sample Results:

![](data/captcha/result/captcha_288.png)

![](data/captcha/result/captcha_435.png)

![](data/captcha/result/captcha_354.png)
