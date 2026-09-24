# Class definitions and labeling policy

## Task

Axis-aligned bounding-box detection of visible rust attached to structural steel. One class: `rust` (ID 0). The output does not distinguish severity or measure corrosion depth, area percentage, section loss or structural capacity.

## Intended rules

- Include clearly visible corrosion attached to steel, including rusty patches, edges, bolts and connections.
- Draw a tight box around a visually coherent rust patch. Separate distinct patches when a meaningful gap exists.
- Avoid boxing an entire component when only a small part is rusty. Avoid redundant nested boxes for the same region.
- Exclude healthy paint, shadows, dirt, loose debris and rust-colored runoff on concrete. Peeling paint alone does not establish rust.
- Review uncertain regions manually; record uncertainty rather than inventing confident labels.
- For genuinely rust-free images, retain the image with an empty label file. Check for missed rust before declaring a negative.

## Current dataset versus intended policy

The frozen adapted Roboflow version 1 has one rust class and 4,107 stored boxes. Source corrosion categories were consolidated in the adapted dataset. The current export still contains broad and overlapping boxes; these rules are a target for future annotation review, not a certification that the dataset has been fully corrected. The training loader removed one duplicate label. No comprehensive relabeling was performed in this assignment run.

## Evaluation

The notebook creates 352 training and 88 validation images from the original export and records the assignments. There is no independent test set. New author photographs are qualitative examples without independently verified ground truth. See [error analysis](error_analysis.md) for selected failures and improvements.
