<div align="center">

# MIVIA-IWDD-500 DATASET

### A PUBLIC VIDEO BENCHMARK FOR AUTOMATED ILLEGAL WASTE DUMPING DETECTION AND TEMPORAL LOCALIZATION

[![Paper](https://img.shields.io/badge/Paper-Image%20and%20Vision%20Computing-1f6feb)](https://doi.org/10.1016/j.imavis.2026.106125)
[![Videos](https://img.shields.io/badge/Videos-500-f97316)](#dataset-at-a-glance)
[![Duration](https://img.shields.io/badge/Footage-%E2%89%883.21%20hours-2ea44f)](#dataset-at-a-glance)
[![Task](https://img.shields.io/badge/Task-Illegal%20Waste%20Dumping%20Detection-8b5cf6)](#task-definition)

<p align="justify"><strong>Mivia-IWDD-500</strong> is a fully balanced public video dataset developed for the <strong>automated detection</strong> and <strong>temporal localization</strong> of illegal waste dumping events in realistic surveillance footage. It comprises <strong>500 videos</strong>, equally divided into <strong>250 positive</strong> and <strong>250 negative</strong> samples. The positive subset is further balanced between <strong>125 static</strong> and <strong>125 dynamic</strong> disposal events, enabling a controlled evaluation across two complementary behavioral modalities.</p>

</div>

---

## TABLE OF CONTENTS

- [OVERVIEW](#overview)
- [TASK DEFINITION](#task-definition)
- [DATASET](#dataset)
- [DATA COLLECTION AND SAMPLE SELECTION](#data-collection-and-sample-selection)
- [ANNOTATION METHODOLOGY](#annotation-methodology)
- [CITATION](#citation)
- [AUTHORS](#authors)

---

## OVERVIEW

<p align="justify"><strong>Illegal Waste Dumping Detection (IWDD)</strong> concerns the automatic recognition of unlawful waste disposal in video streams. The problem cannot be reduced to the static recognition of garbage objects: a reliable system must interpret the <strong>temporally evolving action</strong> through which an object is abandoned and distinguish it from visually similar but legitimate activities. IWDD can therefore be framed as a <strong>domain-specific video-anomaly and action-recognition problem</strong>. <strong>Mivia-IWDD-500</strong> was introduced to address the lack of a publicly available benchmark specifically designed for video-based IWDD. Existing resources have largely focused on static waste images, material classification, abandoned dumpsites, or private video collections, thereby limiting <strong>reproducibility</strong> and <strong>standardized comparison</strong>. The dataset provides a balanced benchmark characterized by heterogeneous surveillance conditions, event-onset annotations, and an official train/test protocol.</p>

## TASK DEFINITION

<p align="justify">The benchmark distinguishes <strong>two complementary disposal modalities</strong>, defined according to the spatial and temporal characteristics of the abandonment action:</p>

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
      <td align="center">Intentional deposition of waste at a selected location. The action is generally <strong>spatially localized</strong> and <strong>temporally well defined</strong>.</td>
      <td align="center">Leaving garbage bags beside a collection point, abandoning furniture, or unloading construction debris and bulky materials.</td>
      <td align="center">The visual evidence may unfold across multiple stages, including approaching the site, placing the object, and leaving the scene.</td>
    </tr>
    <tr>
      <td align="center"><strong>DYNAMIC DISPOSAL</strong></td>
      <td align="center">Brief and spontaneous disposal performed while the subject or vehicle is in motion.</td>
      <td align="center">Throwing waste from a moving vehicle, dropping litter while walking, or releasing a small object while passing.</td>
      <td align="center">The event may occur within a fraction of a second and requires sensitivity to <strong>subtle temporal and motion cues</strong>.</td>
    </tr>
  </tbody>
</table>

</div>

<p align="justify">The benchmark supports <strong>two coupled objectives</strong>: <strong>video-level detection</strong>, which determines whether an illegal dumping event occurs, and <strong>temporal localization</strong>, which estimates the event-onset timestamp in positive videos. This formulation requires models to combine global scene understanding with fine-grained temporal reasoning.</p>

## DATASET

<div align="center">

<table>
  <thead>
    <tr>
      <th align="center" colspan="2">MIVIA-IWDD-500 DATASET SUMMARY</th>
    </tr>
    <tr>
      <th align="center" width="50%">PROPERTY</th>
      <th align="center" width="50%">VALUE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><strong>DATASET NAME</strong></td>
      <td align="center"><strong>MIVIA-IWDD-500</strong></td>
    </tr>
    <tr>
      <td align="center"><strong>TOTAL VIDEOS</strong></td>
      <td align="center"><strong>500</strong></td>
    </tr>
    <tr>
      <td align="center"><strong>TOTAL FOOTAGE</strong></td>
      <td align="center"><strong>APPROXIMATELY 3.21 HOURS</strong></td>
    </tr>
    <tr>
      <td align="center"><strong>POSITIVE VIDEOS</strong></td>
      <td align="center"><strong>250</strong></td>
    </tr>
    <tr>
      <td align="center"><strong>NEGATIVE VIDEOS</strong></td>
      <td align="center"><strong>250</strong></td>
    </tr>
    <tr>
      <td align="center"><strong>STATIC DISPOSAL VIDEOS</strong></td>
      <td align="center"><strong>125</strong></td>
    </tr>
    <tr>
      <td align="center"><strong>DYNAMIC DISPOSAL VIDEOS</strong></td>
      <td align="center"><strong>125</strong></td>
    </tr>
    <tr>
      <td align="center"><strong>OFFICIAL SPLIT</strong></td>
      <td align="center"><strong>400 TRAINING / 100 TEST</strong></td>
    </tr>
  </tbody>
</table>

</div>

## DATA COLLECTION AND SAMPLE SELECTION

<p align="justify">The dataset was constructed through a deliberate collection and curation process designed to represent the environments in which automated IWDD systems are likely to operate. These include <strong>waste collection points</strong>, <strong>public dumping areas</strong>, <strong>roadside zones</strong>, rural or vegetated locations, and other surveillance contexts characterized by variable visibility, scene complexity, and human or vehicle activity.</p>

### POSITIVE SAMPLES

<p align="justify">The majority of positive videos were collected from <strong>real-world surveillance systems</strong>, including both concealed and openly installed cameras. These recordings capture <strong>authentic and unscripted waste-abandonment events</strong> under naturally occurring conditions. The collection process preserves the variability typical of operational surveillance footage, including differences in camera angle, field of view, illumination, time of day, scene clutter, partial occlusion, waste appearance, subject motion, vehicle motion, and the spatial and temporal development of the disposal action.</p>

<p align="justify">The positive subset includes <strong>static disposal events</strong>, such as placing boxes, domestic garbage bags, furniture, construction debris, or bulky materials on the ground, together with <strong>dynamic disposal events</strong>, such as throwing or dropping waste while walking or from a moving vehicle. This composition allows the benchmark to represent both prolonged actions and highly transient behaviors that may occur within a fraction of a second.</p>

### NEGATIVE SAMPLES AND HARD-NEGATIVE CURATION

<p align="justify">Negative-sample selection was treated as a central component of the benchmark design. Rather than including only clearly unrelated activities, the authors deliberately selected <strong>hard negative samples</strong> that resemble illegal dumping in appearance, motion, or context. These videos include subjects who appear to place or drop an object without abandoning it, people carrying bags or boxes, pedestrians or vehicles moving near pre-existing waste, individuals picking up objects from the ground, sanitation workers, garbage trucks, and authorized cleaning operations.</p>

<p align="justify">These confounding scenarios are intended to reduce shortcut learning and false alarms by requiring models to distinguish the <strong>act of illegal abandonment</strong> from ordinary movement, pre-existing waste, and legitimate waste-management activities. Their inclusion makes the negative class operationally meaningful and increases the realism of the benchmark.</p>

## ANNOTATION METHODOLOGY

<p align="justify">All annotations were produced by <strong>human annotators</strong>. For every positive video, the annotation records the exact onset of the disposal event and assigns the event to the static or dynamic taxonomy. The ground-truth onset is defined as the <strong>first frame at which the dumping action becomes visible</strong>, following exhaustive review of the video sequence.</p>

<p align="justify">Each video also includes contextual labels describing the <strong>time of day</strong> and the <strong>illumination condition</strong>. The annotation design is weakly temporal: the event onset is annotated, but the paper explicitly states that dense frame-level annotations are not available. This structure supports both video-level supervision and fine-grained analysis across behavioral and environmental conditions.</p>

### SEMANTIC ANNOTATION COMPONENTS

| Annotation component | Applies to | Domain / representation | Meaning |
|---|---|---|---|
| **Video-level label** | All videos | Binary: dumping / no dumping | Indicates whether the video contains an illegal waste dumping event. |
| **Event-onset timestamp** | Positive videos | Temporal instant, expressed relative to the video timeline | First frame or time instant at which the dumping action becomes visible. |
| **Disposal modality** | Positive videos | `static` or `dynamic` | Distinguishes spatially localized deposition from brief disposal performed in motion. |
| **Time of day** | All videos | `day` or `night` | Describes whether the scene was captured during daytime or nighttime. |
| **Illumination** | All videos | `bright` or `dim` | Describes the prevailing visibility and lighting condition. |

<p align="justify"><strong>Serialization note.</strong> The paper specifies the semantic content of the annotations but does not define the exact on-disk format, filenames, field names, data types, or sentinel values used for negative samples. The public release should therefore include a machine-readable schema or an example annotation that matches the distributed files. No undocumented JSON or CSV structure is assumed in this README.</p>

## CITATION

<p align="justify">When using <strong>Mivia-IWDD-500</strong> in scientific work, please cite the associated publication:</p>

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

<p align="justify"><strong>Paper:</strong> <a href="https://doi.org/10.1016/j.imavis.2026.106125">https://doi.org/10.1016/j.imavis.2026.106125</a></p>

## AUTHORS

<ul>
  <li align="justify"><strong>Antonio Greco</strong> — Department of Information and Electrical Engineering and Applied Mathematics, University of Salerno, Italy</li>
  <li align="justify"><strong>Andrea Vincenzo Ricciardi</strong> — Department of Information and Electrical Engineering and Applied Mathematics, University of Salerno, Italy</li>
  <li align="justify"><strong>Carlo Sansone</strong> — Department of Electrical Engineering and Information Technology, University of Naples Federico II, Italy</li>
  <li align="justify"><strong>Bruno Vento</strong> — Consorzio Interuniversitario Nazionale per l’Informatica (CINI), Italy</li>
</ul>

<p align="justify">All authors contributed equally to the work.</p>

---

<p align="justify"><strong>Mivia-IWDD-500</strong> is intended to support reproducible research on automated illegal waste dumping detection in real-world surveillance video.</p>
