# Dehazing Note

Here will put show notes about **Dehazing Method**.

## Paper

- [A Comprehensive Review on Analysis and Implementation of Recent Image Dehazing Methods](https://doi.org/10.1007/s11831-022-09755-2)

### Introduction

The physical model is given as follows:

$I^C_{hazy}=J^C_{haze-free}T_r(x)+A^C_t(1-T_r(x))$

$T_r(x)=\exp(-\beta d(x))$

$J^C_{haze-free}(x)=\frac{I^c_{hazy}(x)-A^C_t}{T_r(x)}+A^C_t$

Applications of image dehazing:

- video surveillance
- fog related road accidents
- road transportation
- railway transportation
- air transportation
- underwater image enhancement
- remote sensing

Various issues of image dehazing:

- incomplete haze removal
- structure damage
- color shift
- over enhancement

## Recent and popular dehazing methods

## Deep Learning

- physical model
- without physical model

method:

- deep CNN base
- GAN base
- encoder-decoder base(GCANet)
- perceptual pyramid deep network(multi)
- FFA-net with three modules

suffer from darkened or brightened artifacts, file to handle non homogenous haze(thick and thin haze in one image).

## Miscellaneous

- Semi-supervised

  A color constrained dehazing model to produce a *realistic* haze-free image.
  - three networks.
  - RESIDE dataset

- Unsupervised

  Don’t require image pairs.  
  Uses only a single captured hay image to learn.
- Ensemble network

  Can remove the non-homogeneous haze.
- YOLY
  - J(joint)-net
  - T(transmission)-net
  - A(air light) -net

## Non-homogenous Haze

some part of the image is covered with denser haze and other parts with the thin haze.

- KTTD
  - teacher network
  - dehazing network
