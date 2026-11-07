# Research profile (example)

A fictional reader, used for the example archive in this folder.

## The question

Can an open-vocabulary detector find small objects in aerial images (vehicles, boats, small structures) for classes it never saw boxes for, without any box labels for those classes?

## Target

- Venue and deadline: a CVPR-level submission
- Archive title: Small, Unseen, From Above

## Background the maps can assume

DETR-style detectors (DETR, Deformable DETR, DINO), CLIP, the COCO and LVIS protocols, DOTA and xView.

## Your own prior work

A closed-set tiny-object detector for drone footage, trained on VisDrone.

## Axes

- A1 (field map): What supervision do new classes get? values: none / image tags / a few boxes
- A2 (field map): Where does language enter the detector? values: only at the head / fused in the encoder / fused in encoder and decoder
- A3: Where does the vocabulary come from? values: fixed list / free text prompt / mined captions
- A4: Is anything done for small objects? values: nothing / higher resolution / multi-scale or tiling

## Colour-coded concepts

- st1: base classes (seen with boxes)
- st2: novel classes (never seen with boxes)
- st3: missed objects
- st4: background

## Selection rules

- Venues: CVPR, ICCV, ECCV, NeurIPS, or equivalent
- Years: 2021 or newer
- Preprints: allowed only from groups that already publish at those venues
- Code: papers with released code are promoted

## Pace and output

- Pace: two papers a week
- Archive folder: this `examples/` folder
- Publish pages: no
