# SAM exploration — current status

**Author confirmation, 24 September 2026:** SAM has not yet been tested for this project.

No SAM-derived masks, annotation improvements, success claims or failure claims are reported. The earlier Roboflow box-proposal review does not establish that SAM was used. The trained YOLOv8 baseline uses the frozen bounding-box dataset.

## Short experiment still required

The assignment brief requests notes on SAM exploration. To complete those notes, perform a small documented experiment using existing training images, without modifying the baseline dataset or validation split:

1. Select three training images with a clear rust patch, fragmented corrosion, and an ambiguous rust/paint or rust/concrete boundary.
2. Record the actual SAM model/version, tool, image filename and point/box prompts used.
3. Save the original image and mask overlay for each case.
4. Record what the mask included or missed, whether prompt changes helped, and what manual correction would still be needed.
5. Conclude whether the observed masks could assist annotation. Do not generalize beyond the inspected examples.

This is an experiment plan, not experimental evidence. Replace this status note with observed results after the experiment. No improvement to YOLO performance can be attributed to SAM without a separately documented retraining and evaluation experiment.
