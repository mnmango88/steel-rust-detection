# Steel Rust Detection — YOLOv8

**Mohammad Mango | Module 4, Unit 3 | Computer Vision**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mnmango88/steel-rust-detection/blob/main/Steel_Rust_YOLOv8_Colab%20%281%29.ipynb)

## Problem and scope

Detect visible rust on structural steel in inspection photographs to support AECO maintenance review. The model marks candidate rust regions for human inspection; it does not measure section loss, corrosion depth, structural capacity, or safety.

Project success criteria: complete at least 30 training epochs; report validation precision, recall, mAP50 and mAP50–95; produce annotation and prediction evidence; and reproduce the workflow in a fresh Google Colab session without dataset credentials or local software installation. No deployment accuracy target has been established. Current performance supports an academic baseline only.

## Class and annotation rules

One class: **`rust`**, class ID **0**.

The intended rule is to enclose visible corrosion attached to steel as tightly as practical, separating distinct patches when possible. Healthy paint, shadows, dirt, loose debris and runoff stains on concrete should not be labelled as steel rust. Peeling paint alone is insufficient evidence. Ambiguous regions require manual review.

These rules describe the intended policy, not a claim that every inherited annotation meets it. Broad and overlapping source boxes remain a limitation.

## Dataset

- Original source: [Steel Corrosion — University of Tebessa](https://universe.roboflow.com/university-of-tebessa/corrosion-eh3ms).
- Adapted dataset: [Structural Steel Rust BBoxes, version 1](https://universe.roboflow.com/mohammad-mango/structural-steel-rust-bboxes/dataset/1).
- Frozen export: [steel-rust-v1-yolov8.zip.zip](https://github.com/mnmango88/steel-rust-detection/releases/download/v1.0/steel-rust-v1-yolov8.zip.zip). The double extension is the actual asset name.
- Format: YOLOv8 object detection; one `rust` class; 440 images and 4,107 stored bounding boxes.
- Export preprocessing: auto-orientation and stretch resize to 512 × 512; no export augmentations. Training-time augmentations are recorded separately in the generated `train/args.yaml`.
- Dataset license declared by the export: **CC BY 4.0**. Attribution is retained to the original publisher and the adapted Roboflow project; this dataset license does not license third-party software.

ZIP SHA256:

```text
32220278b1b7277d1f662244014b876b7f8298925cec0569ded3decf08aff7b7
```

### Split used for the reported results

| Split | Images | Stored boxes |
|---|---:|---:|
| Train | 352 | 3,400 |
| Validation | 88 | 707 |
| Total | 440 | 4,107 |

The frozen export preserves its original 353 train / 44 validation / 43 test split. The notebook deterministically creates the assignment's 80/20 split: combine the original validation and test sets, then move one training image selected with seed 42 into validation. It saves the exact assignments in `split_manifest.csv`. There is **no independent test set** after this transformation.

Exact pixel-duplicate checks passed. Near-duplicate photographs and shared structures across splits have not been comprehensively audited; validation performance may therefore overestimate generalization to unseen sites. The training loader removed one duplicate label, giving 3,399 effective training boxes from 3,400 stored boxes.

## How to reproduce in Google Colab

1. Open the notebook using the badge above.
2. For a clean test, choose **Runtime → Disconnect and delete runtime** if a session is already connected.
3. Select **Runtime → Change runtime type → T4 GPU**, when available.
4. Choose **Runtime → Run all**, accepting Colab's external-notebook warning after reviewing the code.
5. Wait for training, validation, prediction examples and the final results ZIP download.

No Roboflow account, API key, Colab Secret, Drive mount or manual image upload is required. A Google account is used to access Colab. The notebook downloads the frozen dataset from the public GitHub Release and checks its SHA256 before extraction. Five author-supplied photographs are bundled in the notebook for new-image inference.

The current notebook performs a full **30-epoch run** by default. If Colab denies GPU access, CPU training is possible but substantially slower. Changing the notebook to five epochs does not reproduce the reported 30-epoch result. The trained weights below remain available for inference; a separate inference-only notebook is still to be added.

Expected outputs include:

- `train/weights/best.pt` and `last.pt`, training history and curves;
- `metrics.csv`, validation plots and confusion matrices;
- `evidence/annotations/`: 5 examples;
- `evidence/validation_predictions/`: 10 images;
- `evidence/new_image_predictions/`: 5 images;
- environment, timing, checksum and split records;
- a downloadable `Steel_Rust_Results_<run_id>.zip`.

Outputs are created in the temporary Colab filesystem. Download the results ZIP before the runtime is deleted.

### Reproducibility checklist

- [x] Adapted dataset version 1, source links, public frozen ZIP and SHA256 documented.
- [x] Model: `yolov8n.pt`, fine-tuned for one rust class.
- [x] Epochs: 30; batch: 16; image size: 512; seed: 42.
- [x] Ultralytics pinned to `8.3.221`.
- [x] Runtime versions and `pip freeze` saved by the notebook.
- [x] Fresh GitHub-to-Colab run completed without dataset credentials, as confirmed by the author.

### Reproducibility proof

The author confirmed that the notebook opened from GitHub and completed in a fresh Colab session without Drive authorization, manual uploads or an API key.

- Successful run: **23 September 2026, 13:23:04–13:26:50 UTC**.
- Hardware: **NVIDIA Tesla T4**.
- Completed training epochs: **30**.
- Recorded training call: **207.98 seconds**.
- Recorded session interval: **225.63 seconds**, excluding the earlier package-installation cell.
- Planning estimate: approximately **4–10 minutes on a T4**, including setup/download variability; not a guaranteed runtime.
- Observed environment: Python 3.13.15; PyTorch 2.11.0+cu128; Ultralytics 8.3.221.
- Evidence archive: `Steel_Rust_Results_20260923_132304.zip`.

The archive's automatically generated `fresh_github_reproduction_verified` field remains `false`: the script does not independently verify how the session was launched. The confirmation above records the author's subsequent manual confirmation, supported by the completed run artifacts. The original record is preserved unchanged.

## Results

Validation of the trained weights on **88 images / 707 annotated instances**:

| Metric | Result |
|---|---:|
| Precision | 35.51% |
| Recall | 36.49% |
| mAP50 | 29.23% |
| mAP50–95 | 12.24% |

These values come from the saved standalone validation output, not from rounding the final training epoch. Precision and recall are reported using Ultralytics' validation operating point. Prediction examples use confidence **0.25**; their threshold should not be conflated with the metric reporting point.

Key takeaways:

1. The model detects some visible corrosion, but the precision and recall show substantial false detections and missed annotated regions.
2. The lower mAP50–95 indicates difficulty meeting stricter bounding-box overlap requirements. Inconsistent source box boundaries are a plausible contributor, not a proven sole cause.
3. The five new photographs demonstrate qualitative inference only. They have no independently verified ground-truth labels, so no new-image accuracy metric is claimed.

An earlier Roboflow RF-DETR run used a different validation split. Its metrics are not a controlled comparison with this YOLOv8 baseline.

## Trained weights

[Download best.pt](https://github.com/mnmango88/steel-rust-detection/releases/download/v1.0/best.pt)

SHA256:

```text
42c9db2e7e9f8e4a7b9d0702553d8f5728dac6d5cfd529a5893b0b40888857cb
```

## Limitations and next improvements

Use this prototype to support manual review only. A missed detection cannot establish that steel is corrosion-free, and a positive box does not establish structural damage severity.

Priority improvements are to audit near-duplicates and separate structures/sites across splits; correct inconsistent or overly broad annotations using a shared policy; and expand the dataset with diverse rust examples plus difficult negative images such as healthy steel, paint, dirt and concrete stains. These improvements are proposed, not completed experiments.

## Submission status

Training, validation, prediction evidence generation, public dataset hosting, public weights and the credential-free Colab run are complete. The repository is still being assembled. The following deliverables remain to be added before submission:

- Organized `notebooks/`, `docs/` and `results/` folders, including an inference-only notebook.
- Saved curves, metrics and evidence images in the repository.
- Three documented false positives and three false negatives with image-specific analysis.
- Class definitions, completed governance checklist and SAM exploration notes.
- Explicit project-code licensing and finalized photo-rights documentation, separate from dataset and third-party licenses.
- A 6–8-slide PDF and a mini-report PDF of no more than two pages, linked here.

No final submission-completeness claim is made until these items are present.
