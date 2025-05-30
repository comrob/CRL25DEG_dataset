# Datasets and Technical Details

## Dataset Description

![Dataset overview](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/total.jpeg)
*Visualization of dataset collection areas.*

The datasets consist of multiple recorded loops and calibration sequences intended for evaluation and training of sensor-based localization and mapping.
They were recorded outdoors in challenging localization conditions.
The datasets include LiDAR, GNSS, multiple cameras (RGB, thermal), and IMUs.
**NIR and NDVI are from the Agiception camera.**

---

## Dataset Descriptions

### Public Training Datasets

1. **shellby-0225-train-loop1** (451 m)
   A slightly larger loop in an open field used for training, moving further from trees.

2. **shellby-0225-train-lab**
   A short recording taken in the **Computational Robotics Lab, CTU in Prague** after the experiments for initial testing purposes.
   **Total Station measurements are used as a reference instead of GNSS.**

### Validation Datasets (Submission-enabled)

1. **shellby-0225-validation-loop1** (313 m)
   A small loop primarily for testing submissions. The **forest stays in the range of the 3D LiDAR**.

### Testing Datasets (Final Evaluation)

1. **shellby-0225-test-loop1** (1892 m)
   A large loop containing both field and forest environments.
   Notably, there is a **30-second LiDAR outage** due to a power loss.

2. **shellby-0225-test-loop2** (667 m)
   A loop similar to **shellby-0225-train-loop1** but with a **less smooth trajectory**.
   **Total Station measurements are recorded and will be used for evaluation.**
   The Basler camera is slightly overexposed but still usable.

---

## Data Structure and File Organization

```
├── data
│   ├── train
│   │   ├── extrinsics
│   │   │   ├── extrinsics.txt
│   │   │   ├── static_tf.launch
│   │   │   ├── static_tf.urdf
│   │   ├── <train-sequence-1>
│   │   │   ├── reference
│   │   │   │   ├── <train-sequence-1>.csv
│   │   │   ├── <train-sequence-1>.bag
│   │   ├── <train-sequence-2>/
```

* **<sequence>.bag** → Raw sensory data recorded from the **NUC**.
* **<sequence>.csv** → Reference trajectory in **TUM text format**, no orientation: `x y z qw qx qy qz`.
* [**extrinsics.txt**](https://comrob-ds.fel.cvut.cz:9000/cb-slam/data/train/extrinsics/extrinsics.txt) → Extrinsic calibration data for sensor transformations.
* **static\_tf.launch** → ROS launch file defining static transforms.
* **static\_tf.urdf** → URDF file describing the fixed transformations.

---

## Downloads

* [All training data](https://comrob-ds.fel.cvut.cz:9001/api/v1/buckets/cb-slam/objects/download?prefix=data/train/) (52 GB, about 27 GB for download)
* [extrinsics](https://comrob-ds.fel.cvut.cz:9001/api/v1/buckets/cb-slam/objects/download?prefix=data/train/extrinsics/) (16 kB)
* [shellby-0225-train-lab](https://comrob-ds.fel.cvut.cz:9001/api/v1/buckets/cb-slam/objects/download?prefix=data/train/shellby-0225-train-lab/) (5.5 GB, about 3.3 GB for download)
* [shellby-0225-train-loop1](https://comrob-ds.fel.cvut.cz:9001/api/v1/buckets/cb-slam/objects/download?prefix=data/train/shellby-0225-train-loop1/) (47 GB, about 24 GB for download)

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

*Example of locations where the datasets were collected.*

### Video Teasers

#### Train Dataset

[![Train teaser](https://img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-train-loop1-teaser.mp4)

#### Test Datasets

[![Test loop 1](https://img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-test-loop1-teaser.mp4)

[![Test loop 2](https://img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-test-loop2-teaser.mp4)
