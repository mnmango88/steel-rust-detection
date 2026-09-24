# License scope and attribution

## Project code and model

Copyright (c) 2026 Mohammad Mango. Project notebook code is provided under the GNU Affero General Public License version 3 (AGPL-3.0). The complete license text is in ../LICENSE. Reproduction source is in ../notebooks/ and training settings are in ../results/train/args.yaml.

This project uses Ultralytics 8.3.221 and YOLOv8n. Ultralytics states that its YOLO-trained models follow AGPL-3.0 by default. The published best.pt is distributed on that basis. This notice does not change upstream rights or provide an Enterprise license.

- Upstream version: https://github.com/ultralytics/ultralytics/tree/v8.3.221
- Upstream license: https://github.com/ultralytics/ultralytics/blob/v8.3.221/LICENSE
- Publisher licensing statement: https://www.ultralytics.com/license

## Dataset and derived evidence

The adapted dataset export declares CC BY 4.0. Credit University of Tebessa, Steel Corrosion, via Mohammad Mango's Structural Steel Rust BBoxes version 1. Preserve the source links below and identify modifications when redistributing.

- Original source: https://universe.roboflow.com/university-of-tebessa/corrosion-eh3ms
- Adapted v1: https://universe.roboflow.com/mohammad-mango/structural-steel-rust-bboxes/dataset/1
- License: https://creativecommons.org/licenses/by/4.0/

Representation used here: one rust class, bounding boxes and 512 x 512 export images. The notebook reorganizes the split to 352/88, records a manifest and adds prediction/error overlays. The frozen release retains the exported source bytes. Attribution relies on the export's declared license; this project does not independently establish the original publisher's ownership of each photograph.

## Author photographs and text

Mohammad Mango offers the following five original photographs and original project report/documentation text under CC BY 4.0: Image (39).jpg, Image (41).jpg, Image (42).jpg, Image (45).jpg and Image (49).jpg. Credit: Mohammad Mango, Steel Rust Detection, 2026; https://github.com/mnmango88/steel-rust-detection . Identify changes and retain the license link.

CC BY 4.0 allows sharing and adaptation, including commercial reuse, subject to its terms and attribution. This grant covers the author's rights only. It does not grant rights in third-party software, interface graphics or unrelated material. Roboflow screenshots document the experiment; Roboflow retains rights in its interface elements.

The author reports photographing these examples in a public street where photography was permitted. They are qualitative holdout examples and not client/project photographs. Stock images from earlier trials are excluded from the submitted evidence selection.
