<div align="center">

# MIVIA-IWDD-500 DATASET

### A PUBLIC VIDEO BENCHMARK FOR AUTOMATED ILLEGAL WASTE DUMPING DETECTION AND TEMPORAL LOCALIZATION

[![Paper](https://img.shields.io/badge/PAPER-IMAGE%20AND%20VISION%20COMPUTING-1f6feb)](https://doi.org/10.1016/j.imavis.2026.106125) [![Training Set](https://img.shields.io/badge/TRAINING%20SET-400%20VIDEOS-1f6feb)](https://drive.google.com/drive/folders/1W6YpHQGi6hj8eKSgL6HmSdbk_k8mmVF1?usp=drive_link) [![Public Test Set ID](https://img.shields.io/badge/PUBLIC%20TEST%20SET%20ID-100%20VIDEOS-2ea44f)](https://drive.google.com/drive/folders/1MIj9zelKNDHrPLtzZylHv7leZhxhNIdd?usp=drive_link) [![Contest](https://img.shields.io/badge/CONTEST-IWDD%202026-8b5cf6)](https://mivia.unisa.it/iwddcontest2026/)

<p align="justify">Mivia-IWDD-500 is a fully balanced public video dataset developed for the automated detection and temporal localization of illegal waste dumping events in realistic surveillance footage. It comprises 500 videos, equally divided into 250 positive and 250 negative samples. The positive subset is further balanced between 125 static and 125 dynamic disposal events, enabling a controlled evaluation across two complementary behavioral modalities.</p>

</div>

---

## TABLE OF CONTENTS

- [OVERVIEW](#overview)
- [TASK DEFINITION](#task-definition)
- [DATASET](#dataset)
- [DATA COLLECTION AND SAMPLE SELECTION](#data-collection-and-sample-selection)
- [ANNOTATION METHODOLOGY](#annotation-methodology)
- [ANNOTATION FORMAT](#annotation-format)
- [CITATION](#citation)
- [AUTHORS](#authors)

---

## OVERVIEW

<p align="justify">Illegal Waste Dumping Detection (IWDD) concerns the automatic recognition of unlawful waste disposal in video streams. The problem cannot be reduced to the static recognition of garbage objects: a reliable system must interpret the temporally evolving action through which an object is abandoned and distinguish it from visually similar but legitimate activities. IWDD can therefore be framed as a domain-specific video-anomaly and action-recognition problem. Mivia-IWDD-500 was introduced to address the lack of a publicly available benchmark specifically designed for video-based IWDD. Existing resources have largely focused on static waste images, material classification, abandoned dumpsites, or private video collections, thereby limiting reproducibility and standardized comparison. The dataset provides a balanced benchmark characterized by heterogeneous surveillance conditions, event-onset annotations, and an official train/test protocol.</p>

---

## TASK DEFINITION

<p align="justify">The benchmark distinguishes two complementary disposal modalities, defined according to the spatial and temporal characteristics of the abandonment action:</p>

<div align="center"><table><thead><tr><th align="center" colspan="3">TASK DEFINITION</th></tr><tr><th align="center">MODALITY</th><th align="center">STATIC DUMPING</th><th align="center">DYNAMIC DUMPING</th></tr></thead><tbody><tr><td align="center"><b>DESCRIPTION</b></td><td align="center" nowrap>Waste left at a fixed location.</td><td align="center" nowrap>Waste released while in motion.</td></tr><tr><td align="center"><b>EXAMPLE</b></td><td align="center"><img src="static.gif" width="300" height="169" alt="Static dumping example"></td><td align="center"><img src="dynamic.gif" width="300" height="169" alt="Dynamic dumping example"></td></tr></tbody></table></div>

<p align="justify">The benchmark supports two coupled objectives: video-level detection, which determines whether an illegal dumping event occurs, and temporal localization, which estimates the event-onset timestamp in positive videos. This formulation requires models to combine global scene understanding with fine-grained temporal reasoning.</p>

---

## DATASET

<div align="center"><table><thead><tr><th align="center" colspan="2">MIVIA-IWDD-500&nbsp;DATASET&nbsp;SUMMARY</th></tr><tr><th align="center">PROPERTY</th><th align="center">VALUE</th></tr></thead><tbody><tr><td align="center"><b>DATASET&nbsp;NAME</b></td><td align="center">MIVIA-IWDD-500</td></tr><tr><td align="center"><b>TOTAL&nbsp;VIDEOS</b></td><td align="center">500</td></tr><tr><td align="center"><b>TOTAL&nbsp;FOOTAGE</b></td><td align="center">3&nbsp;HOURS</td></tr><tr><td align="center"><b>POSITIVE&nbsp;VIDEOS</b></td><td align="center">250</td></tr><tr><td align="center"><b>NEGATIVE&nbsp;VIDEOS</b></td><td align="center">250</td></tr><tr><td align="center"><b>STATIC&nbsp;DISPOSAL&nbsp;VIDEOS</b></td><td align="center">125</td></tr><tr><td align="center"><b>DYNAMIC&nbsp;DISPOSAL&nbsp;VIDEOS</b></td><td align="center">125</td></tr><tr><td align="center"><b>OFFICIAL&nbsp;SPLIT</b></td><td align="center">400&nbsp;TRAINING&nbsp;/&nbsp;100&nbsp;TEST</td></tr></tbody></table></div>

---

## DATA COLLECTION AND SAMPLE SELECTION

<p align="justify">The dataset was constructed through a deliberate collection and curation process designed to represent the environments in which automated IWDD systems are likely to operate. These include waste collection points, public dumping areas, roadside zones, rural or vegetated locations, and other surveillance contexts characterized by variable visibility, scene complexity, and human or vehicle activity.</p>

### POSITIVE SAMPLES

<p align="justify">The majority of positive videos were collected from real-world surveillance systems, including both concealed and openly installed cameras. These recordings capture authentic and unscripted waste-abandonment events under naturally occurring conditions. The collection process preserves the variability typical of operational surveillance footage, including differences in camera angle, field of view, illumination, time of day, scene clutter, partial occlusion, waste appearance, subject motion, vehicle motion, and the spatial and temporal development of the disposal action.</p>

<p align="justify">The positive subset includes static disposal events, such as placing boxes, domestic garbage bags, furniture, construction debris, or bulky materials on the ground, together with dynamic disposal events, such as throwing or dropping waste while walking or from a moving vehicle. This composition allows the benchmark to represent both prolonged actions and highly transient behaviors that may occur within a fraction of a second.</p>

### NEGATIVE SAMPLES AND HARD-NEGATIVE CURATION

<p align="justify">Negative-sample selection was treated as a central component of the benchmark design. Rather than including only clearly unrelated activities, the authors deliberately selected hard negative samples that resemble illegal dumping in appearance, motion, or context. These videos include subjects who appear to place or drop an object without abandoning it, people carrying bags or boxes, pedestrians or vehicles moving near pre-existing waste, individuals picking up objects from the ground, sanitation workers, garbage trucks, and authorized cleaning operations.</p>

<p align="justify">These confounding scenarios are intended to reduce shortcut learning and false alarms by requiring models to distinguish the act of illegal abandonment from ordinary movement, pre-existing waste, and legitimate waste-management activities. Their inclusion makes the negative class operationally meaningful and increases the realism of the benchmark.</p>

---

## ANNOTATION METHODOLOGY

<p align="justify">All annotations were produced by human annotators. For every positive video, the annotation records the exact onset of the disposal event and assigns the event to the static or dynamic taxonomy. The ground-truth onset is defined as the first frame at which the dumping action becomes visible, following exhaustive review of the video sequence.</p>

<p align="justify">Each video also includes contextual labels describing the time of day and the illumination condition. The annotation design is weakly temporal: the event onset is annotated, but the paper explicitly states that dense frame-level annotations are not available. This structure supports both video-level supervision and fine-grained analysis across behavioral and environmental conditions.</p>

### SEMANTIC ANNOTATION COMPONENTS

<div align="center"><table><thead><tr><th align="center" colspan="3">SEMANTIC&nbsp;ANNOTATION&nbsp;COMPONENTS</th></tr><tr><th align="center">COMPONENT</th><th align="center">APPLIES&nbsp;TO</th><th align="center">DOMAIN&nbsp;/&nbsp;REPRESENTATION</th></tr></thead><tbody><tr><td align="center"><b>VIDEO-LEVEL&nbsp;LABEL</b></td><td align="center">ALL&nbsp;VIDEOS</td><td align="center"><code>DUMPING</code>&nbsp;/&nbsp;<code>NO&nbsp;DUMPING</code></td></tr><tr><td align="center"><b>EVENT-ONSET&nbsp;TIMESTAMP</b></td><td align="center">POSITIVE&nbsp;VIDEOS</td><td align="center">TIMESTAMP&nbsp;ON&nbsp;VIDEO&nbsp;TIMELINE</td></tr><tr><td align="center"><b>DISPOSAL&nbsp;MODALITY</b></td><td align="center">POSITIVE&nbsp;VIDEOS</td><td align="center"><code>STATIC</code>&nbsp;/&nbsp;<code>DYNAMIC</code></td></tr><tr><td align="center"><b>TIME&nbsp;OF&nbsp;DAY</b></td><td align="center">ALL&nbsp;VIDEOS</td><td align="center"><code>DAY</code>&nbsp;/&nbsp;<code>NIGHT</code></td></tr><tr><td align="center"><b>ILLUMINATION</b></td><td align="center">ALL&nbsp;VIDEOS</td><td align="center"><code>BRIGHT</code>&nbsp;/&nbsp;<code>DIM</code></td></tr></tbody></table></div>

---

## ANNOTATION FORMAT

<p align="justify">Each video in the dataset is released together with a JSON annotation file. The two sample classes share the same structure and differ only in the values of the <code>label</code>, <code>timestamp</code>, and <code>event_type</code> fields.</p>

### NEGATIVE VIDEOS

<p align="justify">Videos that do not contain an illegal dumping event set <code>label</code> to <code>false</code>, use a <code>timestamp</code> of <code>-1</code> to indicate the absence of any event, and set <code>event_type</code> to <code>normal</code>.</p>

```json
{
  "label": "false",
  "timestamp": -1,
  "metadata": {
    "video_id": "vid0005.mp4",
    "resolution": "1920x1080",
    "frame_rate": 29.97,
    "duration": 17.42,
    "event_type": "normal"
  }
}
```

### POSITIVE VIDEOS

<p align="justify">Videos that contain an illegal dumping event set <code>label</code> to <code>true</code>, while <code>timestamp</code> reports, in seconds, the initial instant (onset) of the event. The <code>event_type</code> field takes either <code>static dumping</code> or <code>dynamic dumping</code>.</p>

```json
{
  "label": "true",
  "timestamp": 2,
  "metadata": {
    "video_id": "vid0012.mp4",
    "resolution": "1920x1080",
    "frame_rate": 59.94,
    "duration": 15.63,
    "event_type": "dynamic dumping"
  }
}
```

---

## CITATION

<p align="justify">When using Mivia-IWDD-500 in scientific work, please cite the following publications:</p>

```bibtex
@article{greco2026benchmarking,
  title     = {Benchmarking Illegal Waste Dumping Detection: A Public Video Dataset and a Reference Baseline},
  author    = {Greco, Antonio and Ricciardi, Andrea Vincenzo and Sansone, Carlo and Vento, Bruno},
  journal   = {Image and Vision Computing},
  volume    = {174},
  pages     = {106125},
  year      = {2026}
}

@inproceedings{bouwmans2026illegal,
  title     = {Illegal waste dumping detection},
  author    = {Bouwmans, Thierry and Greco, Antonio and Pierard, Sebastien and Ricciardi, Andrea Vincenzo and Sansone, Carlo and Van Droogenbroeck, Marc and Vento, Bruno},
  booktitle = {Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision},
  pages     = {539--548},
  year      = {2026}
}
```

---

## AUTHORS

<ul><li align="justify">Antonio Greco — DIEM — University of Salerno, ITA — <a href="mailto:agreco@unisa.it">agreco@unisa.it</a></li>
  <li align="justify">Andrea Vincenzo Ricciardi — DIEM — University of Salerno, ITA — <a href="mailto:anricciardi@unisa.it">anricciardi@unisa.it</a></li>
  <li align="justify">Carlo Sansone — DIETI — University of Naples Federico II, ITA — <a href="mailto:carlo.sansone@unina.it">carlo.sansone@unina.it</a></li>
  <li align="justify">Bruno Vento — CINI, ITA — <a href="mailto:brunovento.it@gmail.com">brunovento.it@gmail.com</a></li></ul>

<p align="justify">All authors contributed equally to the work. For any additional requests, clarifications, or information not available in this repository, please do not hesitate to contact us at the e-mail addresses listed above.</p>
