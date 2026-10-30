# Introduction to Computer Vision — Lab Notebooks

Jupyter notebooks for the labs of my *Introduction to Computer Vision* course. The labs
go from CNN transfer learning on skin-lesion images, through classical filtering and
edge detection, to hand-crafted features (HOG, SIFT) and genetic-algorithm feature
selection.

## Notebooks

| Lab | Notebook | What it does | Dataset |
|---|---|---|---|
| 01 | [`Lab01_Skin_Cancer_ISIC.ipynb`](lab01/Lab01_Skin_Cancer_ISIC.ipynb) | Transfer learning with 8 pretrained CNNs (frozen feature extractors), comparison of 7 classical classifiers on the extracted features, and a computational-efficiency comparison | [ISIC 9-class skin cancer](https://www.kaggle.com/datasets/nodoubttome/skin-cancer9-classesisic) |
| 02 | [`Lab02_Skin_Cancer_HAM10000.ipynb`](lab02/Lab02_Skin_Cancer_HAM10000.ipynb) | Effect of spatial filtering (none, average, Gaussian, median, sharpen, Sobel) on a pretrained CNN: 3 backbones × 6 conditions = 18 experiments on one lesion-grouped split | [HAM10000](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000) |
| 03 | [`Lab03_Edge_Detection_HAM10000.ipynb`](lab03/Lab03_Edge_Detection_HAM10000.ipynb) | Edge detection and its impact on classification, compared against the raw (Lab 01) and filtered (Lab 02) inputs | HAM10000 |
| 05 | [`LAB_05_HOG_Defect_Detection.ipynb`](lab05/LAB_05_HOG_Defect_Detection.ipynb) | HOG features + ML classifier for industrial defect detection (binary normal/defective and multi-class) | [NEU steel surface defects](https://www.kaggle.com/datasets/sovitrath/neu-steel-surface-defect-detect-trainvalid-split) |
| 06 | [`Landmark_Recognition_SIFT.ipynb`](lab06/Landmark_Recognition_SIFT.ipynb) | Landmark recognition with SIFT matching, Lowe's ratio test and RANSAC verification, rejection of landmarks not in the database, and localisation of the match | 5 landmarks × 5 reference photos (Wikimedia Commons), supplied as `landmark_dataset.zip` |
| 07 | [`Lab_07_GA_HOG_PneumoniaMNIST.ipynb`](lab07/Lab_07_GA_HOG_PneumoniaMNIST.ipynb) | Does genetic-algorithm feature selection on HOG features beat a plain HOG + RBF-SVM baseline, with fewer features? | [PneumoniaMNIST](https://medmnist.com/) |

Lab 04 (Canny-based lesion boundary detection) has no notebook in this repo.

Each notebook keeps its saved outputs, so the results are visible on GitHub without
re-running anything.

## Running the notebooks

They were written for **Google Colab** and also run locally.

**Colab:** upload a notebook, choose *Runtime → Change runtime type → T4 GPU* (strongly
recommended for the CNN labs 01–03), then *Runtime → Run all*.

**Locally:**

```bash
git clone https://github.com/alinoor4/computer-vision.git
cd computer-vision
pip install numpy scipy pandas matplotlib seaborn pillow scikit-learn scikit-image \
            opencv-python joblib psutil xgboost torch torchvision thop kagglehub \
            python-docx jupyterlab
jupyter lab
```

The datasets are **not** included in this repository:

- Labs 01, 02, 03, 05 download their data with `kagglehub` on first run (you may be asked
  for Kaggle credentials). Each notebook also has a setting to point at a local copy.
- Lab 06 expects `landmark_dataset.zip` (or the extracted `landmark_database/` and
  `query_images/` folders) next to the notebook. It needs OpenCV ≥ 4.4 for SIFT.
- Lab 07 loads PneumoniaMNIST as an `.npz` file.

Lab 02 and Lab 03 reuse the data settings of the earlier labs, so their results are
directly comparable.

## License

[GPL-3.0](LICENSE)
