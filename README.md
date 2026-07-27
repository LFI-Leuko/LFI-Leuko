# LFI-Leuko Dataset

> A comprehensive dataset for detecting and classifying leukocytes and related microorganisms in microscopic images.

📥 **[Download Dataset]([DATASET_LINK])**

> `[https://pan.baidu.com/s/13MPnn_fcK0lYb3NL8n0kcw?pwd=yq2z]`

---

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset Structure](#dataset-structure)
- [Statistics](#statistics)
  - [Hyphae Dataset](#hyphae-dataset)
  - [Large Size Target Dataset](#large-size-target-dataset)
  - [Small Size Target Dataset](#small-size-target-dataset)
- [Data Format](#data-format)
- [Citation](#citation)
- [License](#license)

---

## Overview

**LFI-Leuko** is a large-scale dataset specifically designed for training and evaluating object detection models in the domain of microscopic medical image analysis. The dataset contains images of leukocytes and various microorganisms commonly found in clinical examinations, annotated in YOLO format for direct use with popular object detection frameworks.

### Key Features

- **Three sub-datasets** targeting different detection scenarios
- **YOLO-format annotations** for easy integration with detection frameworks
- **Train/Val/Test split** for standardized evaluation
- **Comprehensive class coverage** of relevant microorganisms

---

## Dataset Structure

```
LFI-Leuko/
├── HyphaeDataset/
│   ├── classes.txt
│   ├── train/
│   │   ├── images/
│   │   └── labels/
│   ├── val/
│   │   ├── images/
│   │   └── labels/
│   └── test/
│       ├── images/
│       └── labels/
│
├── LargeSizeTargetDataset/
│   ├── classes.txt
│   ├── train/
│   │   ├── images/
│   │   └── labels/
│   ├── val/
│   │   ├── images/
│   │   └── labels/
│   └── test/
│       ├── images/
│       └── labels/
│
└── SmallSizeTargetDataset/
    ├── classes.txt
    ├── train/
    │   ├── images/
    │   └── labels/
    ├── val/
    │   ├── images/
    │   └── labels/
    └── test/
        ├── images/
        └── labels/
```

### Data Organization


| Directory     | Description                                        |
| ------------- | -------------------------------------------------- |
| `classes.txt` | List of class names for the dataset (one per line) |
| `train/`      | Training set - 70% of data                         |
| `val/`        | Validation set - ~15% of data                      |
| `test/`       | Test set - ~15% of data                            |
| `images/`     | JPEG images of microscopic samples                 |
| `labels/`     | YOLO-format annotation files (.txt)                |


---

## Statistics

> **Note:** Statistics show the number of bounding box annotations (instances), not the number of images.

### Hyphae Dataset


| Class  | Total | Train | Val | Test | Train % | Val %  | Test % |
| ------ | ----- | ----- | --- | ---- | ------- | ------ | ------ |
| Hyphae | 1,082 | 767   | 139 | 176  | 70.89%  | 12.85% | 16.27% |


**Total Annotations:** 1,082

### Large Size Target Dataset


| Class           | Total  | Train  | Val   | Test  | Train % | Val %  | Test % |
| --------------- | ------ | ------ | ----- | ----- | ------- | ------ | ------ |
| EpithelialCells | 7,729  | 5,348  | 1,174 | 1,207 | 69.19%  | 15.19% | 15.62% |
| ParabasalCells  | 619    | 438    | 108   | 73    | 70.76%  | 17.45% | 11.79% |
| Leukocytes      | 39,761 | 27,953 | 5,611 | 6,197 | 70.30%  | 14.11% | 15.59% |
| Trichomonas     | 2,230  | 1,522  | 371   | 337   | 68.25%  | 16.64% | 15.11% |
| ClueCells       | 376    | 263    | 55    | 58    | 69.95%  | 14.63% | 15.43% |


**Total Annotations:** 50,715

### Small Size Target Dataset


| Class             | Total  | Train  | Val   | Test  | Train % | Val %  | Test % |
| ----------------- | ------ | ------ | ----- | ----- | ------- | ------ | ------ |
| Spores            | 13,127 | 9,834  | 1,961 | 1,332 | 74.91%  | 14.94% | 10.15% |
| Blastospores      | 5,880  | 4,430  | 813   | 637   | 75.34%  | 13.83% | 10.83% |
| Pseudohyphae      | 2,662  | 2,070  | 370   | 222   | 77.76%  | 13.90% | 8.34%  |
| Bacteria          | 61,154 | 42,749 | 8,635 | 9,770 | 69.90%  | 14.12% | 15.98% |
| Cocci             | 15,341 | 10,603 | 2,333 | 2,405 | 69.12%  | 15.21% | 15.68% |
| LacticAcidBacilli | 8,047  | 5,676  | 1,088 | 1,283 | 70.54%  | 13.52% | 15.94% |
| Campylobacter     | 1,884  | 1,347  | 251   | 286   | 71.50%  | 13.32% | 15.18% |

**Total Annotations:** 106,211

---

## Data Format

### Image Format

- **Format:** JPEG (.jpg)
- **Naming:** Images and their corresponding label files share identical filenames (e.g., `image001.jpg` ↔ `image001.txt`)

### Label Format (YOLO)

Each label file contains one annotation per line in the following format:

```
<class_id> <x_center> <y_center> <width> <height>
```

Where:

- `class_id`: Integer ID (0-indexed, corresponds to line number in `classes.txt`)
- `x_center`, `y_center`: Center coordinates normalized to [0, 1]
- `width`, `height`: Dimensions normalized to [0, 1]

### Example classes.txt

```text
class_name_1
class_name_2
class_name_3
```

### Using with YOLO Frameworks

Create a dataset YAML configuration file:

```yaml
# dataset.yaml
path: /path/to/LFI-Leuko/HyphaeDataset
train: train/images
val: val/images
test: test/images

nc: 1  # number of classes
names: ['Hyphae']  # class names
```

---

## Citation

If you use this dataset in your research, please cite:

```bibtex
@misc{LFI-Leuko,
  title = {LFI-Leuko: A Dataset for Leukocyte and Microorganism Detection},
  author = {Gang Lyu, Kai Jiang, Qiang Chen},
  year = {2026},
  howpublished = {\url{https://github.com/LFI-Leuko/LFI-Leuko}},
  note = {Available at: [https://pan.baidu.com/s/13MPnn_fcK0lYb3NL8n0kcw?pwd=yq2z]}
}
```

---

## License

This dataset is released under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/).

- **Allowed:** Use for non-commercial research and educational purposes
- **Required:** Attribution and share-alike

For commercial licensing inquiries, please contact the dataset authors.

---

## Contact

- **GitHub Issues:** [https://github.com/LFI-Leuk/LFI-Leuko/issues](https://github.com/LFI-Leuk/LFI-Leuko/issues)
- **Email:** [lvgang@szut.edu.cn](mailto:lvgang@szut.edu.cn)

---

*Last updated: July 2026*
