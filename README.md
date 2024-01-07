# Refining CNN-Based Electrode Regression with Corner Points
## Abstract

We propose a solution to detect electrode position of  Li-battery. Firstly, we determine the pole area of the battery X-ray image (ROI) through corner point detection, and then use a deep convolution network to regress the poles in the ROI. Finally, the regressed position is optimized and corrected using the corner point prior, which can greatly alleviate the loss of positioning accuracy caused by feature map down-sampling, padding and other operations in the neural network learning process.

## Background

The quality of battery cells is closely related to the position of the electrodes. Due to the multiple levels of cells and the large overlap between electrode sheets, the image collected by X-rays has low brightness, high noise, and different pole area sizes and pole positions. Therefore, accurate pole detection is extremely challenging. The current automated detection algorithm does not fully utilize the X-ray imaging features, resulting in a high overkill rate.

## Contribution

- The pole area (ROI) is quickly determined in high-resolution X-ray images based on corner detection。
- High-resolution neural network (HRNet) with heatmap regression is used to detect pole coordinates,  improving the model adaptability using multiple data enhancement methods.
- A confidence-based adjustment module is proposed to adaptively optimize the pole detection results by evaluating the confidence of the poles predicted by CNN and their reference corners.

## Proposed Framework

![](.\files\framework.png)

## Experimental Result

- Use Oriented-FAST to detect ***N*** corner points.

| Method                        | NME(%)↓   | PCK@0.5%↑ | PCK@1.0%↑ |
| ----------------------------- | --------- | --------- | --------- |
| HRNet                         | 0.658     | 0.422     | 0.818     |
| HRNet + Corner points (N=128) | 0.624     | 0.486     | 0.836     |
| HRNet + Corner points (N=512) | **0.582** | **0.519** | **0.865** |

## **Scalability**

In the task of using deep learning for key point extraction, it's promising to consider combining traditional pixel gradient analysis methods and CNN-based heatmap regression to improve the accuracy or efficiency of the overall solution.

## Citation

```
@misc{rcerwcp,
  author = {Lin Wu},
  title = {Refining CNN-Based Electrode Regression with Corner Points},
  year = {2024},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/fiftywu/CNN-Based-Electrode-Regression}}
}
```