# Governance checklist

**Project:** Steel Rust Detection — Mohammad Mango  
**Review date:** 24 September 2026  
**Scope:** Academic prototype supporting human inspection review.

| Topic | Recorded practice / limitation |
|---|---|
| Dataset provenance | Original University of Tebessa Steel Corrosion dataset, through the adapted Structural Steel Rust BBoxes version 1. The export declares CC BY 4.0; preserve attribution and the adaptation history. |
| Personal photographs | Mohammad Mango states that he took the five new-image examples in a public street where photography was permitted. They are not represented as client/project photographs. This is the author's statement, not an independent legal verification. |
| Privacy and consent | Selected examples focus on steel details; no identifiable people were observed in the reviewed five images. Unrelated uploaded photographs and internet stock examples are excluded from the evidence pack. Permission to photograph is recorded separately from a public redistribution/reuse declaration, which remains to be finalized. |
| Data minimization | Use only the five selected personal examples. Avoid publishing unrelated scenes, identifying location details or unnecessary metadata; confirm metadata before final publication. The notebook already embeds these selected images, so this review applies to both notebook and evidence assets. |
| Credential handling | The primary workflow uses public release URLs and SHA256 verification, with no API key, Secrets or Drive mount required. No credentials are intentionally included. Review committed files and outputs before final submission. |
| Human oversight | Every detection needs human review. No automatic structural acceptance, rejection or maintenance decision. |
| False negatives | Missed rust may leave deterioration unflagged. No detection must never be treated as proof that steel is corrosion-free or safe. |
| False positives | Incorrect or duplicated boxes may cause unnecessary inspection effort. Verify the actual surface and box boundary before acting. |
| Limitations | Low precision/recall; uncertain annotation consistency; no comprehensive near-duplicate/site audit; 88-image validation and no independent test set; only five qualitative personal examples. |
| When not to use | Do not use to certify structural safety, estimate capacity/section loss, assess hidden corrosion, or replace a qualified inspection. |
| Reproducibility | Frozen dataset and weights on GitHub Release. Author confirmed a fresh credential-free GitHub-to-Colab run on 23 September 2026. Original execution records remain unchanged. |
| Licensing | Dataset license declaration and attribution are documented. Project code, trained weights, third-party software and personal photographs require separate, explicit scope statements; these are not automatically covered by the dataset license. |

**Open items before final submission:** finalize the personal-photo publication/reuse statement; check image metadata and committed outputs; finalize project-code and third-party licensing notes. This checklist records completed practices and remaining checks without claiming the latter are complete.
