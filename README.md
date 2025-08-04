# Shellbe: 3D-LiDAR centered multi-sensor dataset in a structurally degraded environment.
### 📚 Table of Contents

* [Competition Links](#competition-links)
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

## Competition Links

* **Official Competition Platform:** [https://comrob-ds.fel.cvut.cz:555/competitions/18/](https://comrob-ds.fel.cvut.cz:555/competitions/18/)
* **Evaluation Framework (slam-bench):** [https://github.com/comrob/slam-bench/tree/main](https://github.com/comrob/slam-bench/tree/main)

---

## Dataset Description

![Dataset overview](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/total.jpeg)
*Visualization of dataset collection areas.*

The datasets consist of multiple recorded loops and calibration sequences intended for evaluation and training of sensor-based localization and mapping. They were recorded outdoors in challenging localization conditions. The datasets include LiDAR, GNSS, multiple cameras (RGB, thermal), and IMUs.
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

The dataset is organized to be compatible with the [slam-bench evaluation framework](https://github.com/comrob/slam-bench/tree/main).

```

<dataset\_name>/
├── calibration/
│   ├── extrinsics/
│   │   ├── extrinsics.txt
│   │   ├── static_tf.launch
│   │   └── static_tf.urdf
│   └── instrinsics/
│       ├── basler.yaml
│       └── ...
├── reference/
│   ├── reference.txt
│   └── ...
├── sensors/
│   └── <all_bagfiles>.bag
└── tracks/
   ├── all.txt
   └── passive.txt

```

* `sensors/<all_bagfiles>.bag` → Raw sensory data in ROS bag files sequence.
* `calibration/` → Contains intrinsic and extrinsic calibration parameters.
* `reference/` → Folder containing the ground-truth reference trajectory.
* `tracks/` → Contains files defining subsets of ROS topics for specific evaluation scenarios (e.g., `passive.txt` might only list topics from non-interfering sensors). The default track is `all`, which plays all sensors.

### Reference Contents

Each dataset contains a `reference/` subdirectory with:
* `reference.txt`: The ground-truth trajectory in TUM format.

---

## Downloads

Training datasets are provided on [GoogleDrive](https://drive.google.com/drive/folders/1ef0k0JzQpKvGQkLGCsqh9FhuewvpQVYq?usp=sharing).

---

## Examples and Teasers

![location1](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location1.jpeg)
![location2](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location2.jpeg)
*Example environments where data was collected.*

### Video Teasers
#### Train Dataset
[![Train teaser](https://img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-train-loop1-teaser.mp4)
#### Test Datasets
[![Test loop 1](https://img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-test-loop1-teaser.mp4)
[![Test loop 2](https://img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-test-loop2-teaser.mp4)
