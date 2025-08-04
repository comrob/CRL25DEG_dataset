### 📚 Table of Contents

* [Dataset Description](#dataset-description)
* [Dataset Descriptions](#dataset-descriptions)

  * [Public Training Datasets](#public-training-datasets)
  * [Validation Datasets](#validation-datasets)
  * [Testing Datasets](#testing-datasets)
* [Data Structure and File Organization](#data-structure-and-file-organization)

  * [Reference Contents](#reference-contents)
* [Downloads](#downloads)
* [Examples and Teasers](#examples-and-teasers)

  * [Video Teasers](#video-teasers)

# Datasets and Technical Details

## Dataset Description

![Dataset overview](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/total.jpeg)
*Visualization of dataset collection areas.*

The datasets consist of multiple recorded loops and calibration sequences intended for evaluation and training of sensor-based localization and mapping.
They were recorded outdoors in challenging localization conditions.
The datasets include LiDAR, GNSS, multiple cameras (RGB, thermal), and IMUs.
**NIR and NDVI are provided by the Agiception camera.**

---

## Dataset Descriptions

### Public Training Datasets

* **shellby-0225-train-loop1** (451 m)
  Loop in an open field used for training, moving further from trees.

* **shellby-0225-train-lab**
  Short indoor recording from **CTU Computational Robotics Lab** for initial testing.
  Uses **Total Station** instead of GNSS.

### Validation Datasets

* **shellby-0225-validation-loop1** (313 m)
  Small loop primarily for testing submissions. The **forest remains in LiDAR range**.

### Testing Datasets

* **shellby-0225-test-loop1** (1892 m)
  Long loop with both field and forest. Includes a **30-second LiDAR outage** due to power loss.

* **shellby-0225-test-loop2** (667 m)
  Similar to the training loop but with **less smooth trajectory**.
  Evaluated using **Total Station** data. Basler camera slightly overexposed.

---

## Data Structure and File Organization

```
data/
├── calibration
│   ├── extrinsics
│   │   ├── extrinsics.txt
│   │   ├── static_tf.launch
│   │   └── static_tf.urdf
│   └── instrinsics
│       ├── basler.yaml
│       ├── flir_boson.yaml
│       ├── plantpix1.yaml
│       └── plantpix2.yaml
├── train
│   ├── calibration
│   ├── shellby-0225-train-lab
│   │   ├── reference
│   │   │   ├── shellby-0225-train-lab.txt
│   │   │   └── shellby-0225-train-lab_noisy.txt
│   │   └── shellby-0225-train-lab.bag
│   └── shellby-0225-train-loop1
├── validation
│   ├── calibration
│   └── shellby-0225-validation-loop1
├── test/...
```

* `<sequence>.bag` → Raw sensory data.
* `reference/` → Folder containing reference trajectories.
* `calibration/extrinsics/` → Transformations between sensor frames.
* `calibration/instrinsics/` → Intrinsic parameters for cameras.
* `static_tf.launch` → ROS static transform launch file.
* `static_tf.urdf` → URDF for static transform definitions.

### Reference Contents

Each dataset contains a `reference/` subdirectory with:

* `*.txt`: Ground-truth trajectory (TUM or Total Station format).
* `*_noisy.txt`: Unfiltered GNSS trajectory (may be degraded by environment).

---

## Downloads

Training datasets are provided on the [GoogleDrive](https://drive.google.com/drive/folders/1ef0k0JzQpKvGQkLGCsqh9FhuewvpQVYq?usp=sharing).

---

## Examples and Teasers

![location1](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location1.jpeg)
![location2](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location2.jpeg)
![location3](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location3.jpeg)
![location4](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location4.jpeg)
![location5](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location5.jpeg)
![location6](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location6.jpeg)
![location7](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location7.jpeg)
![location8](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location8.jpeg)
![location9](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location9.jpeg)

*Example environments where data was collected.*

### Video Teasers

#### Train Dataset

[![Train teaser](https://img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-train-loop1-teaser.mp4)

#### Test Datasets

[![Test loop 1](https://img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-test-loop1-teaser.mp4)

[![Test loop 2](https://img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-test-loop2-teaser.mp4)
