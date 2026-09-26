# VisionLot Data

## Data Source

The VisionLot project will use self-collected photographs of a dealership vehicle inventory parking lot.

Images will be captured from a consistent elevated viewpoint on the seventh floor of the dealership building. This position provides an aerial view of the parking area with clearly visible parking-space boundaries and reduces vehicle-to-vehicle occlusion.

## Planned Dataset Size

The planned dataset will contain approximately 30–50 parking-lot images.

Development will begin with approximately 3–5 sample images to confirm that the pretrained YOLO11 model can successfully detect vehicles before expanding the image collection.

## Region of Interest

The initial proof of concept will monitor approximately 10–20 clearly visible parking spaces rather than the entire parking lot.

Each monitored parking space will receive a unique identifier, such as:

- A01
- A02
- A03
- A04

The same parking-space regions will be used across images captured from the consistent camera viewpoint.

## Ground-Truth Labels

Each monitored parking space will be manually verified and assigned one of two occupancy labels:

- **Occupied** — a vehicle is present in the parking space.
- **Vacant** — no vehicle is present in the parking space.

These labels will serve as the ground truth when evaluating VisionLot's occupancy predictions.

Example:

A01 = Occupied  
A02 = Vacant  
A03 = Occupied  
A04 = Occupied

## Data Collection Plan

Images will be collected at different times so that the dataset contains different parking occupancy patterns.

The initial workflow will be:

1. Collect 3–5 sample images.
2. Test pretrained YOLO11 vehicle detection.
3. Define the parking-space regions.
4. Develop the occupied/vacant classification logic.
5. Expand the collection toward 30–50 images.
6. Manually record the correct occupancy state for the monitored spaces.
7. Use the labeled images to evaluate VisionLot's performance.

## Privacy Considerations

The project does not require identifying individual people or reading vehicle license plates. When practical, identifiable people and readable license plates will be minimized because they are not necessary for parking occupancy detection.

## Dataset Availability

The photographs are being collected specifically for this course project and are not from a public dataset. The dataset will be used to develop and evaluate the VisionLot proof of concept.
