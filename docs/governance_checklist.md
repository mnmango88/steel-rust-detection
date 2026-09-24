# Governance checklist

**Project:** Steel Rust Detection — Mohammad Mango  
**Review date:** 24 September 2026  
**Scope:** Academic prototype supporting human inspection review.

| Topic | Recorded practice / limitation |
|---|---|
| Dataset provenance | Original University of Tebessa Steel Corrosion dataset, through the adapted Structural Steel Rust BBoxes version 1. The export declares CC BY 4.0; preserve attribution and the adaptation history. |
| Personal photographs | Mohammad Mango states that he took the five new-image examples in a public street where photography was permitted. They are not represented as client/project photographs. This is the author's statement, not an independent legal verification. |
| Privacy and consent | Selected examples focus on steel details; no identifiable people were observed in the reviewed five images. Unrelated uploaded photographs and internet stock examples are excluded from the evidence pack. The author-photo CC BY 4.0 reuse terms and their scope are documented in licensing.md. |
| Data minimization | Use only the five selected personal examples. Inspected EXIF tags in the five submitted inputs contain no GPS coordinates. Basic orientation, resolution, dimensions and color-space metadata remain. The training notebook embeds these photos, and inference downloads identical pinned bytes. |
| Credential handling | The primary workflow uses public release URLs and SHA256 verification, with no API key, Secrets or Drive mount required. A targeted pattern scan of 10 commits / 32 unique text blobs found no candidate keys. This is a scoped scan, not proof that every possible secret format is absent. |
| Human oversight | Every detection needs human review. No automatic structural acceptance, rejection or maintenance decision. |
| False negatives | Missed rust may leave deterioration unflagged. No detection must never be treated as proof that steel is corrosion-free or safe. |
| False positives | Incorrect or duplicated boxes may cause unnecessary inspection effort. Verify the actual surface and box boundary before acting. |
| Limitations | Low precision/recall; uncertain annotation consistency; no comprehensive near-duplicate/site audit; 88-image validation and no independent test set; only five qualitative personal examples. |
| When not to use | Do not use to certify structural safety, estimate capacity/section loss, assess hidden corrosion, or replace a qualified inspection. |
| Reproducibility | Frozen dataset and weights on GitHub Release. Author confirmed a fresh credential-free GitHub-to-Colab run on 23 September 2026. Original execution records remain unchanged. |
| Licensing | Dataset license declaration and attribution are documented. Code and model terms are AGPL-3.0; dataset and author-photo terms are CC BY 4.0 as scoped in licensing.md. Third-party rights remain separate. |

**Review scope:** The metadata and targeted credential checks above were completed on the inspected copies and repository history through dc75ea12f04eddec35f2dfc55bb3fb2fa5aab101. Capture permission and authorship rely on the author's statement. Licensing statements apply when adopted and published by the author. Dataset ownership and all possible secret formats have not been independently audited.
