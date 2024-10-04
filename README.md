# Frechet Inception Distance (FID) Calculation for Generative Models

This repository contains a Jupyter notebook (`FID.ipynb`) that demonstrates the calculation of the Frechet Inception Distance (FID) for evaluating generative models, particularly Generative Adversarial Networks (GANs).

## Why FID for Generative Models?

Traditional evaluation metrics used for discriminative models are not suitable for generative models due to the following reasons:

1. Generative models produce new, unique samples rather than predictions on existing data.
2. There's no one-to-one correspondence between generated samples and real data points.
3. We need to assess the quality, diversity, and realism of the generated samples, which requires different metrics.
4. Conventional metrics like accuracy or mean squared error are not applicable to generative tasks.

FID addresses these challenges by providing a meaningful measure of the similarity between generated and real image distributions.

## What is FID?

Frechet Inception Distance (FID) is a metric used to assess the quality of images generated by generative models. It measures how similar the generated images are to real images in terms of their statistical properties.

Key aspects of FID:

1. **Feature Extraction**: Uses a pre-trained Inception v3 network to extract high-level features from both real and generated images.
2. **Distribution Comparison**: Assumes feature vectors follow a multidimensional Gaussian distribution.
3. **Statistical Moments**: Calculates mean and covariance of feature distributions for both real and generated images.
4. **Distance Calculation**: Computes the Frechet distance between the two Gaussian distributions.

The FID score is calculated as:

FID = ||μ_r - μ_g||^2 + Tr(Σ_r + Σ_g - 2√(Σ_r Σ_g))

Where:
- μ_r and μ_g are the mean feature vectors for real and generated images
- Σ_r and Σ_g are the covariance matrices for real and generated images
- Tr denotes the trace of a matrix (sum of diagonal elements)

## Interpretation

- A lower FID score indicates that the generated images are more similar to the real images.
- A score of 0 would mean the two distributions are identical.

## Advantages of FID

- Considers both quality and diversity of generated images
- Correlates well with human judgment of image quality
- More robust than other metrics like Inception Score

## Limitations of FID

- Depends on the choice of the feature extractor (Inception v3)
- May not capture all aspects of image quality or diversity
- Computationally expensive for large datasets

## Contents of the Notebook

The `FID.ipynb` notebook includes:

1. Setup and importing necessary libraries
2. Loading and preprocessing real and generated images
3. Feature extraction using Inception v3
4. Calculation of mean and covariance for real and generated features
5. Implementation of the FID calculation
6. Interpretation of the results

## Usage

To use this notebook:

1. Ensure you have the required dependencies installed (PyTorch, torchvision, numpy, scipy).
2. Load your generator model and real image dataset.
3. Run the cells in order to calculate the FID score for your generative model.

## Conclusion

FID has become a standard evaluation metric in the field of generative models, particularly for image generation tasks. It provides a meaningful measure of the similarity between generated and real image distributions, helping researchers and practitioners assess and improve their generative models.
