# Hybrid Dehazing

A hybrid network, which employs two sub-networks:

- Haze Residual Attention Network
- Detail Refinement Network

It’s a CNN-base method for Single Image Dehazing (SID) task. The method can effectively remove complex haze (Non-homogeneous)and preserve more image details.

## The Network framework

### Haze Residual Attention Network

- SRB
  - $BN*2 + SE$ with Residual Block
- $Conv + SRB*12 + Conv$

### Detail Refinement Network

- CDB
  - $BN*2 + DCL*2$ with Residual Block
- $Conv + CDB*12 + Conv$

### Loss

$L_{Loss} = L^{MSE}_{haze}+L^{MSE}_{detail}+(L^{PL}_{haze}+L^{PL}_{detail})*\lambda$

$\lambda = 0.01$ from ablation study.

## Result

### Dataset

- SOTS
- HazeRD
- NH-HAZE-testing
- HSTS

### Scores

- PSNR
- SSIM
- LPIPS
- DHQI
- FRFSIM

### Ablation Study

- SRB(w/o SE) and CDB(w/o DCL)
- Different loss functions
- learned features and network depths