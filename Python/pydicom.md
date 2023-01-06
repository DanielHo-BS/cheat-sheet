# Pydicom

## Introduction

pydicom: To read DCM file.

Dicom(Digital Imaging in Medicine)

## Usage

```python
from pydicom import dcmread
# Read DCM
filename = '*.dcm'
ds = dcmread(filename)

# Show metadata
print(ds)

# Get the information by HEX
print('Echo time: ', ds[0x18,0x81].value)

# Get Information by field name
print('shape: ',ds.pixel_array.shape)
print('data type: ',ds.pixel_array.dtype)

# Delete field
del ds[0x10,0x10]

# Plot image by matplotlib
import matplotlib.pyplot as plt
plt.imshow(ds.pixel_array)
plt.show()

# save DICOM
ds.save_as("*.dcm")
```

## Reference

[pydicom](https://pydicom.github.io/)

[DCM Table](https://www.dicomlibrary.com/dicom/dicom-tags/)

[Pydicom Example](https://officeguide.cc/python-pydicom-read-edit-dicom-tutorial-examples/)
