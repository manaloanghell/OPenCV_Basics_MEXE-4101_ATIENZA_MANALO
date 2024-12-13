# OPenCV_Basics_MEXE-4101_ATIENZA_MANALO

# Reducing Noise in Photos

## Introduction

In the realm of computer vision, the presence of noise in images can significantly degrade the performance of image processing algorithms. Noise, whether caused by sensor errors, environmental factors, or transmission processes, obscures critical details, making tasks such as object detection, medical image analysis, and feature extraction challenging. Effective noise reduction techniques are essential to enhance the quality and reliability of visual data for downstream applications, particularly in sensitive domains like healthcare and surveillance.

## Abstract

This project aims to explore and implement multiple noise reduction techniques to enhance the quality of grayscale images and CT scans. By employing methods such as Median Filtering, Gaussian Blurring, and Non-Local Means (NLM), the project demonstrates how different approaches address specific noise types while preserving important image details. Using Python and OpenCV, the project's methodology involves iterative application of these techniques to achieve optimal noise reduction, particularly for medical images. The results are evaluated visually and quantitatively, showcasing the strengths and limitations of each method.

## Project Methods
- **Clone and set up the project repository containing necessary image datasets and dependencies.**
  - Use Git to access the pre-organized folder structure.
  - Load grayscale images of CT scans for processing.

- **Implement a noise reduction function in Python using OpenCV:**
  - Accept a list of methods, including Median Filtering, Gaussian Blurring, and NLM, as input parameters.
  - Apply methods sequentially or individually based on the specified order.

### Method-Specific Implementations
- **Median Filtering:**
  - Replace each pixel’s value with the median value of its neighborhood.
  - Kernel size can be adjusted to tailor the filtering strength.
- **Gaussian Blurring:**
  - Convolve the image with a Gaussian kernel to reduce Gaussian noise.
  - Adjust the kernel size and standard deviation for varying noise levels.
- **Non-Local Means (NLM):**
  - Identify and average similar patches across the image.
  - Tune parameters such as h (filter strength), templateWindowSize, and searchWindowSize for optimal detail preservation.
  - Comparative visualization highlighting the strengths and weaknesses of each method.

## Process Images Using Predefined Methods for Specific Test Cases
- **Case 1:** Apply NLM to address random noise in medical images.
- **Case 2:** Use Gaussian and Median Filtering for mixed noise types.
- **Case 3:** Combine all methods sequentially for comprehensive noise reduction.

### Visualize and Compare Results
- Display side-by-side comparisons of original and processed images.
- Generate plots to highlight the differences in noise reduction efficiency.

## Conclusion

This project highlights the importance of selecting appropriate noise reduction techniques based on the type and intensity of noise. Median Filtering proved effective for salt-and-pepper noise, Gaussian Blurring addressed Gaussian noise, and NLM excelled in preserving fine details while reducing general noise.

Challenges included balancing noise removal and detail preservation, as overly aggressive filtering led to loss of critical image features.

The project’s outcomes emphasize the role of parameter tuning and method selection in achieving optimal results for specific use cases, particularly in medical imaging.

## Additional Materials

### Code:
```python
def reduce_noise(image, methods, kernel_size=5):
    denoised_image = image.copy()

    for method in methods:
        if method == "median":
            denoised_image = cv2.medianBlur(denoised_image, kernel_size)
        elif method == "gaussian":
            denoised_image = cv2.GaussianBlur(denoised_image, (kernel_size, kernel_size), 0)
        elif method == "nlm":
            denoised_image = cv2.fastNlMeansDenoising(denoised_image, None, 20, 7, 21)

    return denoised_image
```

### Images:
- Processed images showing results after Median Filtering, Gaussian Blurring, and NLM.
  ![image](https://github.com/user-attachments/assets/45b9bc26-5bcf-4cd1-bce1-3dd69cb6e760)

  ![image](https://github.com/user-attachments/assets/06d2fa1a-658a-4cd5-a124-d0b441037077)

  ![image](https://github.com/user-attachments/assets/8bc82375-f520-4c0a-8511-ee3b163c5bc2)

  ![image](https://github.com/user-attachments/assets/657a8aa7-9006-4b3c-b36e-2c31b785582c)

  ![image](https://github.com/user-attachments/assets/f37b3452-7d8b-4467-a073-93ef879988a2)

  ![image](https://github.com/user-attachments/assets/8d4e9918-98db-4c8a-a2a5-7560a67bba7e)

  ![image](https://github.com/user-attachments/assets/719e8515-1661-493a-8cb5-478736262acb)

  ![image](https://github.com/user-attachments/assets/bde08b1c-bf64-404e-91af-3487be7f0043)
  
  ![image](https://github.com/user-attachments/assets/15129dc1-d805-4f93-a760-1770e58824b4)

### Video: 
<h5 align="center">
</p> 
 <a href="https://drive.google.com/file/d/1BjSn3awoFOqsAd_8_E44cSKhYpeomx94/view?usp=sharing">
    <source media="(prefers-color-scheme: dark)" srcset="https://github.com/user-attachments/assets/e0b74f47-b346-42cd-95dc-0573035cf7ba">
    <img src="https://github.com/user-attachments/assets/1482220f-3b80-4163-9290-c94174b40ce2" alt="Running of the program" width = 600 title="Running of the program">
</a>   

### Results:
1. **Case 1**: NLM successfully reduced random noise while retaining sharpness.
2. **Case 2**: Gaussian and Median Filtering removed mixed noise but slightly blurred edges.
3. **Case 3**: Sequential application of all methods yielded the cleanest result with minimal detail loss.

## References: 
- OpenCV Tutorial - Easy run on Colab with Code ( https://youtu.be/E3Lg4aZVCAU?si=xgf0MYFIbE3V6UgB)
- Datasets : (https://www.algomedica.com/noise-reduction-ct-scan-gallery)

