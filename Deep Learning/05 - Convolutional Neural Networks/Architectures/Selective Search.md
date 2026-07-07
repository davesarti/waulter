---
tags:
  - deep-learning
  - architecture
year: 2013
task: object-detection
---
**Selective Search** is an image segmentation algorithm used to generate **region proposals** (Regions of Interest, RoI) for object recognition. It acts as a preprocessing step: instead of scanning every possible window, it proposes candidate regions likely to contain objects.

It is a **fixed algorithm** — it does not adapt to the data or the network. 

## Key Features

- **Groups similar pixels together** to form regions, then combines them hierarchically into larger segments
- **Preliminary step**: identifies candidate areas that might contain objects before classification
- Uses a hierarchical approach — pixels are grouped by specific criteria to form a "tree" of segments, from which bounding boxes are derived
- Assigns a **likelihood score** to each region: regions with low likelihood are unlikely to contain the object of interest