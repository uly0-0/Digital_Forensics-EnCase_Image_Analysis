# Digital Forensics — EnCase Image Analysis

This repository documents a complete digital forensic investigation conducted on a NIST CFReDS forensic test image. The project follows real-world forensic methodology, encompassing evidence acquisition, hash verification, chain of custody documentation, artifact recovery using Autopsy and Sleuth Kit, and a formal written examination report.

The test image included a guided worksheet designed to direct a full forensic analysis aimed at uncovering the activities performed by the system's user. That worksheet was meant to serve as a structural framework for this investigation but I decided in the end not to follow it. Instead it was supplemented by independent analytical methods and thorough documentation of the tools and methodologies employed. The analysis covers deleted file recovery, keyword searches, timeline construction, and identification of hidden files and executables.

**Forensic Test Image:** https://cfreds.nist.gov/all/DFIR_AB/ForensicsImageTestimage

---

## Chain of Custody Log

In a real-world forensic investigation, evidence collection is accompanied by a chain of custody form — a written record documenting who handled an evidence item, when, where it was stored, and the reason for each transfer. The documentation included in the repo demonstrates that evidence was maintained under controlled conditions from collection through presentation.

A chain of custody template from [Elite Digital Forensics](https://elitedigitalforensics.com/free-chain-of-custody-form-computer/) was completed prior to beginning the investigation.

### Evidence Directory Structure

The following directory structure was used to organize all case materials on the external evidence drive:

```
CaseName\
    evidence\
        original_image.dd     -- read-only original; never modified
    working\
        copy_image.dd         -- all analysis performed on this copy
    hashes\
        hashes.txt            -- MD5 + SHA-256 of original image
    autopsy_case\
        CaseName.aut          -- Autopsy case file
        CaseName\             -- Autopsy-generated data directory
    reports\
        chain-of-custody\
            2020JimmWilson-Chain-of-Custody
        email-headers\
            email.eml         -- raw email headers
        evidence-inventory\
            evidence doc      -- original evidence extracts
        evidence-notes\
            evidence.md       -- per-artifact notes
        image-evidence\
            originals\
                original.jpg  -- source image with metadata intact
            screenshots\
                screenshot.jpg
            working-copies\
                originalcopy.jpg
        case_notes.txt
        evidence_report.pdf
```

All notes were taken in Obsidian and stored as Markdown files under the `reports/` directory. Supporting screenshots are co-located with their respective notes.

---

## Investigation Steps

### 1. Evidence Acquisition

- The disk image was provided in E01 format.
- Integrity was verified using MD5 and SHA-1 hashes.
- Hashes were recorded in `hashes/hashes.txt`. Evidence hashes were extracted using autopsy built in extraction feature and placed into an excel file under `/evidence-inventory/`
- A working copy was created and its hash verified against the stored value to confirm integrity before analysis began.

The matching hashes confirm the working copy is an unaltered duplicate of the original image.

An evidence inventory spreadsheet exported from Autopsy — containing a full log of extracted artifacts along with their metadata and hashes — is available under `/evidence-inventory/`.

### 2. Analysis in Autopsy

- The verified working image was loaded into Autopsy for analysis.

Autopsy categorizes artifacts into distinct sections (e.g., email messages, Recycle Bin, web history), enabling targeted review without manually traversing the entire directory tree.
Autopsy's tagging system was used throughout the review to flag items of interest. Artifacts with evidentiary value were tagged as **Notable** and subsequently examined individually using a standardized note format.

### 3. Reporting

All findings were compiled into a Markdown draft to facilitate iterative editing, which was then finalized into a formal case report which is included in this repo.