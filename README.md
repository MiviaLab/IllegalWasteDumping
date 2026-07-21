<div align="center">
# MIVIA-IWDD-500 DATASET

### A PUBLIC VIDEO BENCHMARK FOR AUTOMATED ILLEGAL WASTE DUMPING DETECTION AND TEMPORAL LOCALIZATION

[![Paper](https://img.shields.io/badge/Paper-Image%20and%20Vision%20Computing-1f6feb)](https://doi.org/10.1016/j.imavis.2026.106125) [![Videos](https://img.shields.io/badge/Videos-500-f97316)](#dataset) [![Duration](https://img.shields.io/badge/Footage-%E2%89%883.21%20hours-2ea44f)](#dataset) [![Task](https://img.shields.io/badge/Task-Illegal%20Waste%20Dumping%20Detection-8b5cf6)](#task-definition)

<p align="justify">Mivia-IWDD-500 is a fully balanced public video dataset developed for the automated detection and temporal localization of illegal waste dumping events in realistic surveillance footage. It comprises 500 videos, equally divided into 250 positive and 250 negative samples. The positive subset is further balanced between 125 static and 125 dynamic disposal events, enabling a controlled evaluation across two complementary behavioral modalities.</p>
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

<p align="justify">Illegal Waste Dumping Detection (IWDD) concerns the automatic recognition of unlawful waste disposal in video streams. The problem cannot be reduced to the static recognition of garbage objects: a reliable system must interpret the temporally evolving action through which an object is abandoned and distinguish it from visually similar but legitimate activities. IWDD can therefore be framed as a domain-specific video-anomaly and action-recognition problem. Mivia-IWDD-500 was introduced to address the lack of a publicly available benchmark specifically designed for video-based IWDD. Existing resources have largely focused on static waste images, material classification, abandoned dumpsites, or private video collections, thereby limiting reproducibility and standardized comparison. The dataset provides a balanced benchmark characterized by heterogeneous surveillance conditions, event-onset annotations, and an official train/test protocol.</p>

## TASK DEFINITION

<p align="justify">The benchmark distinguishes two complementary disposal modalities, defined according to the spatial and temporal characteristics of the abandonment action:</p>

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

<p align="justify">The benchmark supports two coupled objectives: video-level detection, which determines whether an illegal dumping event occurs, and temporal localization, which estimates the event-onset timestamp in positive videos. This formulation requires models to combine global scene understanding with fine-grained temporal reasoning.</p>

## DATASET

<div align="center">
<table>
<thead>
<tr><th align="center" colspan="2" nowrap><strong>MIVIA-IWDD-500&nbsp;DATASET&nbsp;SUMMARY</strong></th></tr>
<tr><th align="center" width="50%" nowrap><strong>PROPERTY</strong></th><th align="center" width="50%" nowrap><strong>VALUE</strong></th></tr>
</thead>
<tbody>
<tr><td align="center" nowrap><strong>DATASET&nbsp;NAME</strong></td><td align="center" nowrap><strong>MIVIA-IWDD-500</strong></td></tr>
<tr><td align="center" nowrap><strong>TOTAL&nbsp;VIDEOS</strong></td><td align="center" nowrap><strong>500</strong></td></tr>
<tr><td align="center" nowrap><strong>TOTAL&nbsp;FOOTAGE</strong></td><td align="center" nowrap><strong>APPROXIMATELY&nbsp;3.21&nbsp;HOURS</strong></td></tr>
<tr><td align="center" nowrap><strong>POSITIVE&nbsp;VIDEOS</strong></td><td align="center" nowrap><strong>250</strong></td></tr>
<tr><td align="center" nowrap><strong>NEGATIVE&nbsp;VIDEOS</strong></td><td align="center" nowrap><strong>250</strong></td></tr>
<tr><td align="center" nowrap><strong>STATIC&nbsp;DISPOSAL&nbsp;VIDEOS</strong></td><td align="center" nowrap><strong>125</strong></td></tr>
<tr><td align="center" nowrap><strong>DYNAMIC&nbsp;DISPOSAL&nbsp;VIDEOS</strong></td><td align="center" nowrap><strong>125</strong></td></tr>
<tr><td align="center" nowrap><strong>OFFICIAL&nbsp;SPLIT</strong></td><td align="center" nowrap><strong>400&nbsp;TRAINING&nbsp;/&nbsp;100&nbsp;TEST</strong></td></tr>
</tbody>
</table>
</div>

## DATA COLLECTION AND SAMPLE SELECTION

<p align="justify">The dataset was constructed through a deliberate collection and curation process designed to represent the environments in which automated IWDD systems are likely to operate. These include waste collection points, public dumping areas, roadside zones, rural or vegetated locations, and other surveillance contexts characterized by variable visibility, scene complexity, and human or vehicle activity.</p>

### POSITIVE SAMPLES

<p align="justify">The majority of positive videos were collected from real-world surveillance systems, including both concealed and openly installed cameras. These recordings capture authentic and unscripted waste-abandonment events under naturally occurring conditions. The collection process preserves the variability typical of operational surveillance footage, including differences in camera angle, field of view, illumination, time of day, scene clutter, partial occlusion, waste appearance, subject motion, vehicle motion, and the spatial and temporal development of the disposal action.</p>
<p align="justify">The positive subset includes static disposal events, such as placing boxes, domestic garbage bags, furniture, construction debris, or bulky materials on the ground, together with dynamic disposal events, such as throwing or dropping waste while walking or from a moving vehicle. This composition allows the benchmark to represent both prolonged actions and highly transient behaviors that may occur within a fraction of a second.</p>

### NEGATIVE SAMPLES AND HARD-NEGATIVE CURATION

<p align="justify">Negative-sample selection was treated as a central component of the benchmark design. Rather than including only clearly unrelated activities, the authors deliberately selected hard negative samples that resemble illegal dumping in appearance, motion, or context. These videos include subjects who appear to place or drop an object without abandoning it, people carrying bags or boxes, pedestrians or vehicles moving near pre-existing waste, individuals picking up objects from the ground, sanitation workers, garbage trucks, and authorized cleaning operations.</p>
<p align="justify">These confounding scenarios are intended to reduce shortcut learning and false alarms by requiring models to distinguish the act of illegal abandonment from ordinary movement, pre-existing waste, and legitimate waste-management activities. Their inclusion makes the negative class operationally meaningful and increases the realism of the benchmark.</p>

## ANNOTATION METHODOLOGY

<p align="justify">All annotations were produced by human annotators. For every positive video, the annotation records the exact onset of the disposal event and assigns the event to the static or dynamic taxonomy. The ground-truth onset is defined as the first frame at which the dumping action becomes visible, following exhaustive review of the video sequence.</p>
<p align="justify">Each video also includes contextual labels describing the time of day and the illumination condition. The annotation design is weakly temporal: the event onset is annotated, but the paper explicitly states that dense frame-level annotations are not available. This structure supports both video-level supervision and fine-grained analysis across behavioral and environmental conditions.</p>

### SEMANTIC ANNOTATION COMPONENTS

<div align="center">
<table>
<thead>
<tr><th align="center" colspan="3"><strong>SEMANTIC ANNOTATION COMPONENTS</strong></th></tr>
<tr><th align="center" width="34%"><strong>ANNOTATION COMPONENT</strong></th><th align="center" width="22%"><strong>APPLIES TO</strong></th><th align="center" width="44%"><strong>DOMAIN / REPRESENTATION</strong></th></tr>
</thead>
<tbody>
<tr><td align="center"><strong>VIDEO-LEVEL LABEL</strong></td><td align="center"><strong>ALL VIDEOS</strong></td><td align="center"><strong>BINARY: DUMPING / NO DUMPING</strong></td></tr>
<tr><td align="center"><strong>EVENT-ONSET TIMESTAMP</strong></td><td align="center"><strong>POSITIVE VIDEOS</strong></td><td align="center"><strong>TEMPORAL INSTANT RELATIVE TO THE VIDEO TIMELINE</strong></td></tr>
<tr><td align="center"><strong>DISPOSAL MODALITY</strong></td><td align="center"><strong>POSITIVE VIDEOS</strong></td><td align="center"><strong>STATIC / DYNAMIC</strong></td></tr>
<tr><td align="center"><strong>TIME OF DAY</strong></td><td align="center"><strong>ALL VIDEOS</strong></td><td align="center"><strong>DAY / NIGHT</strong></td></tr>
<tr><td align="center"><strong>ILLUMINATION</strong></td><td align="center"><strong>ALL VIDEOS</strong></td><td align="center"><strong>BRIGHT / DIM</strong></td></tr>
</tbody>
</table>
</div>

<p align="justify">Serialization note. The paper specifies the semantic content of the annotations but does not define the exact on-disk format, filenames, field names, data types, or sentinel values used for negative samples. The public release should therefore include a machine-readable schema or an example annotation that matches the distributed files. No undocumented JSON or CSV structure is assumed in this README.</p>

## CITATION

<p align="justify">When using Mivia-IWDD-500 in scientific work, please cite the associated publication:</p>

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

<p align="justify">Paper: <a href="https://doi.org/10.1016/j.imavis.2026.106125">https://doi.org/10.1016/j.imavis.2026.106125</a></p>

## AUTHORS

<ul>
  <li align="justify">Antonio Greco — Department of Information and Electrical Engineering and Applied Mathematics, University of Salerno, Italy</li>
  <li align="justify">Andrea Vincenzo Ricciardi — Department of Information and Electrical Engineering and Applied Mathematics, University of Salerno, Italy</li>
  <li align="justify">Carlo Sansone — Department of Electrical Engineering and Information Technology, University of Naples Federico II, Italy</li>
  <li align="justify">Bruno Vento — Consorzio Interuniversitario Nazionale per l’Informatica (CINI), Italy</li>
</ul>

<p align="justify">All authors contributed equally to the work.</p>

---

<p align="justify">Mivia-IWDD-500 is intended to support reproducible research on automated illegal waste dumping detection in real-world surveillance video.</p>
