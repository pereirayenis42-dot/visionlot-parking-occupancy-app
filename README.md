# VisionLot: Dealership Parking Occupancy Detector

**Student:** Yenis Pereira  
**Course:** ITAI 1378 – Computer Vision and AI  
**Project Tier:** Tier 1 – Core Project

## Project Overview

VisionLot is a computer vision application designed to monitor parking-space occupancy in a dealership vehicle inventory lot. The system will analyze images taken from a consistent elevated viewpoint and determine which monitored parking spaces are occupied or vacant.

## Tier Selection

I selected **Tier 1 – Core Project** because VisionLot uses a pretrained object detection model to solve a focused computer vision problem. The project can be developed and tested using free resources such as Google Colab without requiring a large custom-trained model or paid computing resources.

## Problem Statement

Vehicle locations at a dealership may be recorded when inventory is parked, but those records can become outdated when vehicles are moved without their new location being reported. This can require employees, particularly in the new-car and sales departments, to physically search designated inventory areas for vehicles that are no longer where they are expected to be. VisionLot will explore how computer vision can provide a visual record of parking-space occupancy that could eventually help identify changes in vehicle inventory locations.

## Solution Overview

VisionLot will analyze photographs of a dealership inventory parking area taken from a consistent elevated viewpoint. A pretrained YOLO11 object detection model will locate vehicles in the image, and the application will compare those detections with predefined parking-space regions to determine whether each monitored space is occupied or vacant.

**System Flow:**

Parking Lot Image → YOLO11 Vehicle Detection → Parking-Space Regions → Occupancy Analysis → Visual Occupancy Report

## Technical Approach

VisionLot will use **object detection** and parking-space occupancy analysis to determine whether predefined spaces in a dealership inventory lot are occupied or vacant.

- **Computer Vision Technique:** Object Detection
- **Model:** Pretrained YOLO11
- **Programming Language:** Python
- **Framework/Tools:** Ultralytics YOLO, OpenCV, and Google Colab
- **Input:** Images of the dealership inventory parking lot taken from a consistent elevated viewpoint
- **Output:** An annotated image showing monitored parking spaces as occupied or vacant, along with an occupancy summary

YOLO11 will be used to detect vehicles within each parking-lot image. OpenCV and Python will be used to define the parking-space regions and compare vehicle detections with those regions. If a detected vehicle sufficiently overlaps a predefined parking space, the application will mark that space as occupied; otherwise, it will be marked as vacant.

A pretrained YOLO11 model was selected because the initial goal is to detect common vehicle classes rather than train a new object detector from scratch. This keeps the project achievable as a Tier 1 application while still allowing custom application logic to be developed for the dealership parking environment.

## Data Plan

The project will use a **self-collected image dataset** from a dealership vehicle inventory parking lot. Images will be taken from a consistent elevated position on the seventh-floor of the dealership building overlooking the parking area. Using a consistent viewpoint will allow the same predefined parking-space regions to be applied across multiple images.

### Data Source
- Self-collected photographs of the dealership inventory parking lot
- Images taken from approximately the same seventh-floor camera position
- Photographs collected at different times to capture changes in parking occupancy
- No public dataset is required for the initial proof of concept

### Estimated Dataset Size
The initial dataset will contain approximately **30–50 images**. Development will begin with only a few sample images to confirm that the complete detection and occupancy pipeline works before expanding the dataset.

### Monitored Area
The first version of VisionLot will focus on approximately **10–20 clearly visible parking spaces** rather than attempting to analyze the entire parking lot. Each monitored parking space will receive a unique identifier such as A01, A02, A03, and so on.

### Labels
Each monitored parking space will have a ground-truth occupancy label:

- **Occupied** — a vehicle is physically present in the parking space
- **Vacant** — no vehicle is present in the parking space

For example:

A01 = Occupied  
A02 = Vacant  
A03 = Occupied

These manually verified labels will be compared with VisionLot's predictions when evaluating the system.

### Data Collection Considerations
Images will be collected under different parking conditions so that the system can be tested when different spaces become occupied or vacant. When practical, identifiable people and readable license plates will be minimized because they are not required for the parking-occupancy task.

## Success Metrics

VisionLot will be evaluated using measurable performance targets to determine whether the parking occupancy system successfully meets its objective.

### Primary Metric: Parking-Space Occupancy Accuracy

The primary success metric will be the percentage of monitored parking spaces that VisionLot correctly identifies as either **occupied** or **vacant**.

**Target: At least 90% occupancy classification accuracy.**

Accuracy will be calculated by comparing the system's prediction for each parking space with manually verified ground-truth labels.

Accuracy = (Correct Occupancy Predictions / Total Parking-Space Predictions) × 100

For example, if VisionLot evaluates 150 parking-space instances across multiple images and correctly identifies 138 of them:

Accuracy = (138 / 150) × 100 = 92%

The project will be considered successful if it achieves at least 90% occupancy accuracy on the evaluation images.

### Secondary Metric: Processing Time

The secondary metric will measure how long VisionLot takes to process one parking-lot image and generate its occupancy results.

**Target: Process each image in 2 seconds or less using Google Colab.**

Processing time will include vehicle detection and parking-space occupancy analysis. This metric will help determine whether the system could eventually support more frequent parking-lot monitoring.

## Milestone Plan

VisionLot will be developed in phases so that a basic working computer vision pipeline is established before expanding the dataset or adding additional application logic.

| Phase | Goal | VisionLot Milestone |
|---|---|---|
| 🧭 Blueprint | Define and plan the project | Complete the project proposal, GitHub repository, technical approach, data plan, success metrics, and project roadmap. |
| 🔌 First Working Demo | Get a pretrained model running end-to-end on a few sample images | Run pretrained YOLO11 on 3–5 dealership parking-lot images and confirm that vehicles can be detected successfully. |
| 🛠 Make It Yours | Add project-specific data and application logic | Define approximately 10–20 parking spaces, assign space IDs, create occupied/vacant ground-truth labels, and develop the logic that determines whether each space is occupied. Expand the image collection toward approximately 30–50 images. |
| 📈 Improve and Measure | Test, troubleshoot, and evaluate the system | Test VisionLot on multiple parking conditions, correct problems with parking-space regions or detection thresholds, measure occupancy accuracy, and record processing time. |
| 🎥 Package and Present | Prepare the final proof of concept | Complete the GitHub README and documentation, prepare the final presentation and demo, and demonstrate VisionLot processing dealership parking-lot images from input to occupancy report. |

## Risks, Plan B, and Resources

### Risk 1: Vehicles May Be Difficult to Detect From the Elevated Viewpoint

Because images will be captured from the seventh floor, vehicles will appear smaller than they would in a ground-level photograph. Distance, partial obstruction, shadows, and lighting conditions may cause YOLO11 to miss some vehicles.

**Plan B:** VisionLot will initially focus on a smaller Region of Interest containing approximately 10–20 clearly visible parking spaces. Images can be cropped to this area before detection so that the monitored vehicles occupy a larger portion of the image. The YOLO confidence threshold may also be evaluated and adjusted if necessary.

### Risk 2: Camera Position May Change Between Images

VisionLot relies on predefined parking-space regions. If photographs are taken from significantly different positions or angles, the parking-space coordinates may no longer align correctly with the painted spaces.

**Plan B:** Images will be captured from the same seventh-floor location using the same phone orientation and approximately the same camera angle. Consistent landmarks will be used to reproduce the viewpoint. If small alignment differences occur, images may be cropped or aligned before occupancy analysis.

### Additional Limitation: Occlusion and Unusual Parking

Vehicles that are partially blocked by trees, poles, other vehicles, or landscaping may be more difficult to detect. Vehicles parked outside normal parking-space boundaries may also make occupancy decisions less reliable.

The initial proof of concept will therefore prioritize parking spaces with clear visibility. More difficult areas can be explored as a future improvement after the basic system works reliably.

### Resources

- **Development Environment:** Google Colab
- **Programming Language:** Python
- **Object Detection Model:** Pretrained YOLO11
- **Computer Vision Tools:** Ultralytics YOLO and OpenCV
- **Data Source:** Self-collected dealership parking-lot photographs
- **Camera:** Smartphone camera
- **Compute:** Google Colab free-tier CPU/GPU resources
- **Estimated Cost:** $0

The project is designed to remain achievable using free computing resources and an existing pretrained model.
