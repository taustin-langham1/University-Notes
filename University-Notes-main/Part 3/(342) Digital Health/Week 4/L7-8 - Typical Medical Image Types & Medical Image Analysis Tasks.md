
high frequency = more variation

**Learning Objectives** 
- understand the main types of medical images and their characteristics
- Learn about key medical image analysis tasks and their applications
- explore the role of digital imaging in modern healthcare


## Medical Images

• Today’s medical field is highly dependent on extensive image-based data acquisition.

• This differs from traditional computer vision, which primarily uses cameras and range sensors.

• Medical imaging instead leverages specialized modalities, including:

• X-ray fluoroscopy
• Computed Tomography (CT)
• Magnetic Resonance Imaging (MRI)
• Ultrasound imaging


**Diagnostic Radiography (X-ray)** 

utilises ionizing radiation (X-Rays) to capture images of different anatomical structures throughout the body

• Employ ionizing radiation to examine anatomical structures and
physical characteristics in both human and animal patients.
• Diagnostic radiography serves as the foundational technology, upon
which many other imaging modalities are based.

 Different body tissues have varying densities and
thicknesses, resulting in differential X-ray absorption
patterns.
✓ Dense structures like bones absorb most of the
radiation, appearing white on radiographic images.
✓ Less dense tissues such as lungs allow more radiation to
pass through, creating grey appearances.
➢ Medical professionals interpret these varying contrast
levels and patterns to identify and diagnose medical
conditions.

**Computed Tomography (CT)**

Creates cross-sectional slices that can be reconstructed into three-dimensional anatomical images

• CT scanning employs a rotating X-ray system
that captures cross-sectional images or “slices”
from multiple angles around the body.
• This technology can effectively image various
anatomical regions, including brain, neck, chest,
abdomen, pelvis, and extremities.
• The resulting 3D reconstructions enable
physicians to diagnose fractures, strokes,
malignancies, and other pathological conditions.

**Magnetic Resonance Imaging (MRI)**

Employs powerful magnetic and radio-frequency pulses to generate detailed images of internal organs and soft tissues

• MRI harnesses the magnetic characteristics of hydrogen atoms within the
body, to generate detailed images.
• The technology employs extremely powerful superconducting magnets, and
can capture images in any anatomical plane.
• As a highly effective diagnostic modality, MRI excels at visualizing soft tissues
including muscles, cartilage, and fat, without exposing patients to ionizing
radiation (Thus, an MRI scan is a painless and safe procedure)


**Sonography (Ultrasound)**

Uses high-frequency sound waves to produce real-time images of tissues, organs, and blood vessels

• Ultrasound employs acoustic waves to examine,
treat, and access specific body regions.
• High-frequency sound waves are directed
toward target areas, and the reflected echoes
are captured and processed.
• It is a non-invasive technique, and requires no
ionizing radiation exposure.
• Ultrasound can serve both diagnostic and
therapeutic roles in evaluating organ
dysfunction.

## Gray scale image 

**2D array**
256 possible values {0,1,..,256}, 1 byte for each pixel, 8 bits
resolution (e.g., 1920 (columns, width), 1080 (rows, height))
Quantized to have a finite number of possible values (256)
	- sometimes standardised to 0..1 (B&W)
	- value 0 = black
	- value 1 = white

**rgb grey value**

0.299 R + 0.587 G + 0.114 B


RGB, (256, 256, 256) - 16 million possible shades of colour

![[Pasted image 20251030130630.png]]

## Filtering (Convolution)


### Image Filtering 

- image filtering is an image processing operation
- Can be used to **remove some unwanted information**
- Can be used to **extract useful information**
- Linear filtering:
	- The output is a linear combination of pixel values in some neighbourhood


Filtering is an essential operation in deep neural networks

**Effect of filtering in deep networks:**
- Remove some unwanted information and extract useful information over layer in the deep network


- Correlation / Convolution (precisely, they have subtle differences)

- Convolution - mathematically significantly different due to flipping
	- flipping is skipped for convolution in this course
	- thus is we say convolution we mean correlation

 

- Filtering (convolution) operation
- Slide the filter kernel over the entire image to produce the output (image / activation)

![[Pasted image 20251030131407.png]]


**Stride** : the step when sliding the filter (kernel) over the input

Stride = 1 
(sliding step size = 1)

Stride = 2
(sliding step size = 2)


## Edge detection

We can use image filtering to extract useful information: edge
Edge: Significant change in intensity values

Why edge detection:
	edge provides important shape information: fundamental in understanding the image
	after detecting the edge, we can sharpen the edge to improve visual quality


Edge detection: **Prewitt Operator** (as the filter kernel/mask)
	detect horizontal edge, vertical edge
	compute the difference of the neighboring pixels to indicate the likelihood of edges
	![[Pasted image 20251030132025.png]]


## Noise and denoising 

Additive Gaussian Noise

I_distorted = I_original + n

Noise: high spatial frequency
Denoising: low-pass filtering to remove the signal component with high spatial frequencies

we can use mean filter to do denoising, i.e., averaging all the pixels in the neighbourhood covered by the kernel

### Denioising with median filter

Median filter is a non-linear filtering: use the median of all the pixels in a neighbourhood, as the output e.g., Median(2, 80, 6) -> 6

Similar to mean filter, median filter can also be used for denoising 
mean filter is often used to handle "pepper-and-salt" noise

![[Pasted image 20251030132444.png]]


## Question:

What is the function of low-pass (high pass) filtering?


List a filter kernel that can be used for **denoising**

Median / Mean filter

List a filter kernel that can be used for **edge detection**

Prewitt Operator

What is the purpose of padding?


