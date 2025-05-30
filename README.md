<div style="
    box-sizing: border-box;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    line-height: 1.5;
    background: linear-gradient(to right, #1a2e4d, #107acc);
    background-repeat: no-repeat;
    color: gray;"
>

<div style="
    padding: 5%;
    text-align: justify;
    background-color: white;"
>

<h1 style="color: #1a2e4d;">Datasets and Technical Details</h1>

<h2 style="color: #1a2e4d;">Dataset Description</h2>

<figure>
    <img width="100%" src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/total.jpeg"/>
    <figcaption>Visualization of dataset collection areas.</figcaption>
</figure>

The datasets consist of multiple recorded loops and calibration sequences intended for evaluation and training of sensor-based localization and mapping. 
It was recorded outdoors in challenging localization conditions. 
The datasets include LiDAR, GNSS, multiple cameras (RGB, thermal), and IMUs. <strong>NIR and NDVI are from the Agiception camera.</strong>

<h3 style="color: #1a2e4d;">Dataset Descriptions</h3>

<h4 style="color: #1a2e4d;">Public Training Datasets</h4>
<ol><li><strong>shellby-0225-train-loop1</strong> (451 m) - A slightly larger loop in an open field used for training, moving further from trees.</li>
<li><strong>shellby-0225-train-lab</strong> - A short recording taken in the <strong>Computational Robotics Lab, CTU in Prague</strong> after the experiments for initial testing purposes. <strong>Total Station measurements are used as a reference instead of GNSS.</strong></li>
</ol>

<h4 style="color: #1a2e4d;">Validation Datasets (Submission-enabled)</h4>
<ol>
<li><strong>shellby-0225-validation-loop1</strong> (313 m) - A small loop primarily for testing submissions. The <strong>forest stays in the range of the 3D LiDAR</strong>.</li>
</ol>

<h4 style="color: #1a2e4d;">Testing Datasets (Final Evaluation)</h4>
<ol>
<li><strong>shellby-0225-test-loop1</strong> (1892 m) - A large loop containing both field and forest environments. Notably, there is a <strong>30-second LiDAR outage</strong> due to a power loss.</li>
<li><strong>shellby-0225-test-loop2</strong> (667 m) - A loop similar to <strong>shellby-0225-train-loop1</strong> but with a <strong>less smooth trajectory</strong>. <strong>Total Station Measurements are recorded and will be used for evaluation.</strong> The Basler camera is slightly overexposed but still usable.</li></ol>

<h4 style="color: #1a2e4d;">Data Structure and File Organization</h4>

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

<ul>
<li><strong><sequence>.bag</strong> → Raw sensory data recorded from the <strong>NUC</strong>.</li>
<li><strong><sequence>.csv</strong> → Reference trajectory in <strong>TUM text format</strong>, no orientation: <code>x y z qw qx qy qz</code>.</li>
<li><strong><a href="https://comrob-ds.fel.cvut.cz:9000/cb-slam/data/train/extrinsics/extrinsics.txt">extrinsics.txt</a></strong> → Extrinsic calibration data for sensor transformations.</li>
<li><strong>static_tf.launch</strong> → ROS launch file defining static transforms.</li>
<li><strong>static_tf.urdf</strong> → URDF file describing the fixed transformations.</li>
</ul>

<h4 style="color: #1a2e4d;">Downloads</h4>
<ul>
<li><a href="https://comrob-ds.fel.cvut.cz:9001/api/v1/buckets/cb-slam/objects/download?prefix=data/train/">All training data</a> ( 52 GB, about 27 GB for download)</li>
<li><a href="https://comrob-ds.fel.cvut.cz:9001/api/v1/buckets/cb-slam/objects/download?prefix=data/train/extrinsics/">extrinsics</a> (16 kB)</li>
<li><a href="https://comrob-ds.fel.cvut.cz:9001/api/v1/buckets/cb-slam/objects/download?prefix=data/train/shellby-0225-train-lab/">shellby-0225-train-lab</a> ( 5.5 GB, about 3.3 GB for download)</li>
<li><a href="https://comrob-ds.fel.cvut.cz:9001/api/v1/buckets/cb-slam/objects/download?prefix=data/train/shellby-0225-train-loop1/">shellby-0225-train-loop1 </a> ( 47 GB, about 24 GB for download)</li>
</ul>
					
	
<h3 style="color: #1a2e4d;">Examples and Teasers</h3>

<div style="display: grid; gap:10px;
  grid-template-columns: repeat(3, 1fr);">
    <div style="margin:0;padding:0;">
        <img width="100%" src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location1.jpeg"/>
        <img width="100%" src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location2.jpeg"/>
        <img width="100%" src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location3.jpeg"/>
    </div>
    <div style="">
        <img width="100%" src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location4.jpeg"/>
        <img width="100%" src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location5.jpeg"/>
        <img width="100%" src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location6.jpeg"/>
    </div>
    <div style="">
        <img width="100%" src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location7.jpeg"/>
        <img width="100%" src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location8.jpeg"/>
        <img width="100%" src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/images/location9.jpeg"/>
    </div>
</div>
Example of locations where the datasets were collected.

<figure>
    <video width="100%" controls>
        <source src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-train-loop1-teaser.mp4">
    </video>
    <figcaption>Train dataset teaser - shellby-0225-train-loop.</figcaption>
</figure>

<figure>
    <video width="100%" controls>
        <source src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-test-loop1-teaser.mp4">
    </video>
    <figcaption>Test dataset teaser - shellby-0225-test-loop.</figcaption>
</figure>

<figure>
    <video width="100%" controls>
        <source src="https://comrob-ds.fel.cvut.cz:9000/cb-slam/media/videos/shellby-0225-test-loop2-teaser.mp4">
    </video>
    <figcaption>Test dataset teaser - shellby-0225-test-loop.</figcaption>
</figure>

</div>
</div>
