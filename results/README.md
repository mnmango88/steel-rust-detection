# Results and evidence

Source run: `20260923_132304`, 23 September 2026, Tesla T4, YOLOv8n, 30 epochs.

## Contents

- `metrics.csv`: standalone validation metrics on 88 images and 707 instances.
- `train/results.csv`, `train/results.png`, `train/args.yaml`: training history, curves and configuration.
- `validation/`: validation curves, confusion matrices and batch visualizations.
- `evidence/annotations/`: five examples of inherited dataset annotations, not a claim of label correctness.
- `evidence/validation_predictions/`: ten validation prediction images at confidence 0.25.
- `evidence/new_image_inputs/` and `evidence/new_image_predictions/`: five author-supplied photographs and their predictions. These are qualitative examples without independently verified ground truth.
- `split_manifest.csv`: exact 352/88 assignments. A `test__` filename prefix records the original export split; these images belong to validation in this run, not an independent test set.
- `environment.json`, `pip_freeze.txt`, `run_record.json`: environment and execution evidence.

## Reported metrics

Precision 0.3550807433; recall 0.3649222065; mAP50 0.2922774966; mAP50-95 0.1223626783.

The metric reporting operating point is not necessarily the 0.25 threshold used for prediction screenshots. Missing prediction text files mean zero saved detections; corresponding image evidence is retained.

## Reproducibility confirmation

The author confirmed on 24 September 2026 that the 23 September run opened from GitHub in a fresh Colab session and completed without a Roboflow API key, Colab Secrets, Drive mount or manual uploads. The original automatically generated `fresh_github_reproduction_verified: false` value is preserved: it is not a runtime failure, and the script cannot establish the launch procedure. This note records the subsequent manual confirmation.

The session interval was 225.63 seconds, excluding the package installation cell. The training call took 207.98 seconds.

## Provenance and rights

Dataset examples derive from [University of Tebessa](https://universe.roboflow.com/university-of-tebessa/corrosion-eh3ms), through [Mohammad Mango's adapted version 1](https://universe.roboflow.com/mohammad-mango/structural-steel-rust-bboxes/dataset/1). The export declares CC BY 4.0. The five new photographs were supplied by Mohammad Mango, who stated that he took them; they are separate from the Roboflow dataset. Their public-sharing permissions and reuse terms should be recorded in the final governance documentation.

Weights and the full training dataset are hosted as GitHub Release assets rather than duplicated here. File contents copied from the evidence archive are unchanged. Absolute paths inside the saved training configuration describe the original Colab run and are historical records, not portable reproduction paths.
