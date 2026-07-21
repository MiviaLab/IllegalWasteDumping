<div align="center">

# MIVIA-IWDD-500 DATASET

### A PUBLIC VIDEO BENCHMARK FOR AUTOMATED ILLEGAL WASTE DUMPING DETECTION AND TEMPORAL LOCALIZATION

[![Paper](https://img.shields.io/badge/Paper-Image%20and%20Vision%20Computing-1f6feb)](https://doi.org/10.1016/j.imavis.2026.106125)
[![Videos](https://img.shields.io/badge/Videos-500-f97316)](#dataset-at-a-glance)
[![Duration](https://img.shields.io/badge/Footage-%E2%89%883.21%20hours-2ea44f)](#dataset-at-a-glance)
[![Task](https://img.shields.io/badge/Task-Illegal%20Waste%20Dumping%20Detection-8b5cf6)](#task-definition)

**Mivia-IWDD-500** is a *fully balanced public video dataset* designed for the **automated detection** and **temporal localization** of illegal waste dumping events in realistic surveillance footage. It comprises **500 videos**, equally divided into **250 positive** and **250 negative** samples. The positive subset is itself balanced between **125 static** and **125 dynamic** disposal events.

</div>

---

## TABLE OF CONTENTS

- [OVERVIEW](#overview)
- [TASK DEFINITION](#task-definition)
- [DATASET AT A GLANCE](#dataset-at-a-glance)
- [DATA COLLECTION AND SAMPLE SELECTION](#data-collection-and-sample-selection)
- [ANNOTATION METHODOLOGY](#annotation-methodology)
- [CITATION](#citation)
- [AUTHORS](#authors)

---

## OVERVIEW

**Illegal Waste Dumping Detection (IWDD)** concerns the *automatic recognition of unlawful waste disposal in video streams*. The problem cannot be reduced to the static recognition of garbage objects: a reliable system must interpret the **temporally evolving action** through which an object is abandoned and distinguish it from visually similar but *legitimate activities*. IWDD can therefore be framed as a **domain-specific video-anomaly and action-recognition problem**. **Mivia-IWDD-500** was introduced to address the lack of a *publicly available benchmark* specifically designed for video-based IWDD. Existing resources have largely focused on static waste images, material classification, abandoned dumpsites, or private video collections, thereby limiting **reproducibility** and **standardized comparison**. Mivia-IWDD-500 provides a public benchmark characterized by a *balanced class distribution*, *heterogeneous surveillance conditions*, **event-onset annotations**, and an **official train/test protocol**.

## TASK DEFINITION

The benchmark distinguishes **two complementary disposal modalities**, defined according to the *spatial and temporal characteristics of the abandonment action*:

<div align="center">

<table>
  <thead>
    <tr>
      <th align="center" width="16%">MODALITY</th>
      <th align="center" width="28%">DEFINITION</th>
      <th align="center" width="28%">REPRESENTATIVE EXAMPLES</th>
      <th align="center" width="28%">MAIN DETECTION CHALLENGE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><strong>STATIC DISPOSAL</strong></td>
      <td align="center">Intentional deposition of waste at a <em>selected location</em>. The action is generally <strong>spatially localized</strong> and <strong>temporally well defined</strong>.</td>
      <td align="center">Leaving garbage bags beside a collection point, abandoning furniture, or unloading construction debris and bulky materials.</td>
      <td align="center">The visual evidence may unfold across <em>multiple stages</em>, including approaching the site, placing the object, and leaving the scene.</td>
    </tr>
    <tr>
      <td align="center"><strong>DYNAMIC DISPOSAL</strong></td>
      <td align="center">Brief and spontaneous disposal performed while the subject or vehicle is <em>in motion</em>.</td>
      <td align="center">Throwing waste from a moving vehicle, dropping litter while walking, or releasing a small object while passing.</td>
      <td align="center">The event may occur within a <em>fraction of a second</em> and requires sensitivity to <strong>subtle temporal and motion cues</strong>.</td>
    </tr>
  </tbody>
</table>

</div>

The benchmark supports **two coupled objectives**: **video-level detection**, which determines whether an illegal dumping event occurs, and **temporal localization**, which estimates the *event-onset timestamp* in positive videos.

## DATASET AT A GLANCE

| Property | Value |
|---|---:|
| Dataset name | **Mivia-IWDD-500** |
| Total videos | **500** |
| Total footage | **Approximately 3.21 hours** |
| Positive videos | **250** |
| Negative videos | **250** |
| Static disposal videos | **125** |
| Dynamic disposal videos | **125** |
| Daytime videos | **450** |
| Nighttime videos | **50** |
| Bright-condition videos | **472** |
| Dim-condition videos | **28** |
| Official split | **400 training / 100 test** |
| Validation split | **Not specified in the paper** |
| Resolution range | **320×240 to 4096×2160** |
| Most common resolutions | **1920×1080 (45.2%)**, **1280×720 (24.8%)** |
| Typical frame-rate range | **Most videos: 20–30 FPS** |
| Typical clip duration | **The majority are slightly under 20 seconds** |
| Approximate mean duration | **≈23.1 seconds per video**, derived from the reported total duration |

## DATA COLLECTION AND SAMPLE SELECTION

The dataset was constructed through a deliberate collection and curation process intended to represent the environments in which automated IWDD systems are likely to operate, including waste collection points, public dumping areas, roadside zones, rural or vegetated locations, and other surveillance contexts.

### POSITIVE SAMPLES

The majority of positive videos were collected from **real-world surveillance systems**, including both concealed and openly installed cameras. These recordings capture authentic, unscripted waste-abandonment events under naturally occurring conditions. The collection was designed to preserve the variability typical of operational surveillance footage, including differences in:

- camera angle and field of view;
- illumination and time of day;
- scene complexity, clutter, visibility, and partial occlusion;
- waste type, scale, and appearance;
- subject and vehicle motion;
- spatial and temporal characteristics of the disposal action.

The positive subset covers static actions such as placing boxes, domestic garbage bags, furniture, construction debris, or bulky materials on the ground, as well as dynamic actions such as throwing or dropping waste while walking or from a moving vehicle.

### NEGATIVE SAMPLES AND HARD-NEGATIVE CURATION

Negative-sample selection was treated as a central part of the benchmark design. Rather than collecting only obviously unrelated activities, the authors deliberately selected **hard negatives** that resemble illegal dumping in appearance, motion, or context. These include:

- subjects appearing to place or drop an object without abandoning it;
- people carrying bags, backpacks, or boxes;
- pedestrians or vehicles moving near waste that was already present when the recording began;
- subjects picking up objects from the ground;
- sanitation workers, garbage trucks, and authorized cleaning operations.

These confounding cases are intended to reduce shortcut learning and false alarms by forcing models to distinguish the act of illegal abandonment from ordinary movement, pre-existing waste, and legitimate waste-management activities.

```mermaid
flowchart LR
    A[Target real-world IWDD contexts] --> B[Collect heterogeneous video candidates]
    B --> C{Human review and selection}
    C -->|Illegal disposal| D[Positive sample]
    C -->|No illegal disposal| E[Hard negative sample]
    D --> F[Static or dynamic taxonomy]
    E --> G[Confounding and legitimate activities]
    F --> H[Human temporal and contextual annotation]
    G --> H
    H --> I[Balanced train/test benchmark]
```

## ANNOTATION METHODOLOGY

All annotations were produced by **human annotators**. For every positive video, the annotation records the exact onset of the disposal event and assigns the event to the static or dynamic taxonomy. The ground-truth onset is defined as the **first frame at which the dumping action becomes visible**, following exhaustive review.

Each video also includes contextual labels describing the time of day and illumination condition. The annotation design is weakly temporal: the event onset is annotated, but the paper explicitly states that dense frame-level annotations are not available.

### SEMANTIC ANNOTATION COMPONENTS

| Annotation component | Applies to | Domain / representation | Meaning |
|---|---|---|---|
| **Video-level label** | All videos | Binary: dumping / no dumping | Indicates whether the video contains an illegal waste dumping event. |
| **Event-onset timestamp** | Positive videos | Temporal instant, expressed relative to the video timeline | First frame or time instant at which the dumping action becomes visible. |
| **Disposal modality** | Positive videos | `static` or `dynamic` | Distinguishes spatially localized deposition from brief disposal performed in motion. |
| **Time of day** | All videos | `day` or `night` | Describes whether the scene was captured during daytime or nighttime. |
| **Illumination** | All videos | `bright` or `dim` | Describes the prevailing visibility and lighting condition. |

> **Serialization note.** The paper specifies the semantic content of the annotations but does not define the exact on-disk format, filenames, field names, data types, or sentinel values used for negative samples. The public release should therefore include a machine-readable schema or example annotation that matches the distributed files. No undocumented JSON or CSV structure is assumed in this README.


## CITATION

When using Mivia-IWDD-500, please cite:

```bibtex
@article{greco2026benchmarking,
  title   = {Benchmarking Illegal Waste Dumping Detection: A Public Video Dataset and a Reference Baseline},
  author  = {Greco, Antonio and Ricciardi, Andrea Vincenzo and Sansone, Carlo and Vento, Bruno},
  journal = {Image and Vision Computing},
  volume  = {174},
  pages   = {106125},
  year    = {2026},
  doi     = {10.1016/j.imavis.2026.106125}
}
```

**Paper:** [https://doi.org/10.1016/j.imavis.2026.106125](https://doi.org/10.1016/j.imavis.2026.106125)

## AUTHORS

- **Antonio Greco** — Department of Information and Electrical Engineering and Applied Mathematics, University of Salerno, Italy
- **Andrea Vincenzo Ricciardi** — Department of Information and Electrical Engineering and Applied Mathematics, University of Salerno, Italy
- **Carlo Sansone** — Department of Electrical Engineering and Information Technology, University of Naples Federico II, Italy
- **Bruno Vento** — Consorzio Interuniversitario Nazionale per l’Informatica (CINI), Italy

All authors contributed equally to the work.

---

<div align="center">

Mivia-IWDD-500 · Public benchmark for reproducible illegal waste dumping detection research

</div>
