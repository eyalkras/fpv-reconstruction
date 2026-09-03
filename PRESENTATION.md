# FPV Reconstruction - Review Package

This repository contains the finished relative-reconstruction baseline and its compact supporting evidence.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1TIZ76z9lq0SDqArLEEBL9D3V-mILEmNX)

## Open these in order

Use the **Download** links below. GitHub's inline PDF preview can show an error
even when a PDF is valid; these links open the original verified files directly.

1. [Download the project guide](https://github.com/eyalkras/fpv-reconstruction/raw/refs/heads/main/docs/FPV_Project_Guide.pdf) - concise project explanation.
2. [Download the example run](https://github.com/eyalkras/fpv-reconstruction/raw/refs/heads/main/docs/FPV_Example_Run.pdf) - visual walkthrough from a video URL to the final outputs.
3. [Download the validation summary](https://github.com/eyalkras/fpv-reconstruction/raw/refs/heads/main/docs/FPV_Validation_Summary.pdf) - one-page evidence summary across four representative videos.
4. [`notebooks/FPV_Reconstruction.ipynb`](notebooks/FPV_Reconstruction.ipynb) - clean canonical Colab notebook.

## Live notebook

Use the **Open in Colab** button above. It opens the verified runnable Drive copy; GitHub keeps the clean, output-free source version.

Use a T4 GPU or better, add a Hugging Face read token as the Colab secret `HF_TOKEN`, paste one direct video URL, and choose **Runtime -> Run all**.

Before external review, grant the reviewer access to this private GitHub repository, the shared Colab notebook, and the linked Drive evidence folders.

## Example evidence

The clearest example is the Adaissah run. Its complete GLB, PNG, CSV, JSON, and ZIP outputs are stored in [Google Drive](https://drive.google.com/drive/folders/1mYRF8jyh3WjBN6N8kyG46DhMjD7qshsF).

The full four-video evidence table and links are in [`validation/REPORT.md`](validation/REPORT.md).

## Current scope

The baseline produces relative 3D reconstruction and relative camera XYZ. It does not yet claim metres, physical speed, latitude, longitude, or altitude.
