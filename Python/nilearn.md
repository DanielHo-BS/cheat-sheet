# Nilearn

## Introduction

Nilearn enables approachable and versatile analyses of brain volumes,

## Usage

```python
import nibabel as nib
# Read file
img = nib.load(file)
img_array = img.get_fdata()

# Quickly plot
from nilearn import plotting
plotting.plot_img(FILE_PATH)

# Visualizing one volume in a 4D file
from nilearn import image
print(image.load_img(file).shape)
```

## Reference

[Nilearn](https://nilearn.github.io/stable/index.html)