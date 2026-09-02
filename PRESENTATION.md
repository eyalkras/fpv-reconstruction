# FPV Reconstruction - Review Package

This repository contains the finished relative-reconstruction baseline and its compact supporting evidence.

## Open these in order

1. [`docs/FPV_Project_Guide.pdf`](docs/FPV_Project_Guide.pdf) - concise project explanation.
2. [`docs/FPV_Example_Run.pdf`](docs/FPV_Example_Run.pdf) - visual walkthrough from a video URL to the final outputs.
3. [`docs/FPV_Validation_Summary.pdf`](docs/FPV_Validation_Summary.pdf) - one-page evidence summary across four representative videos.
4. [`notebooks/FPV_Reconstruction.ipynb`](notebooks/FPV_Reconstruction.ipynb) - clean canonical Colab notebook.

## Live notebook

Open the shared notebook in [Google Colab](https://colab.research.google.com/drive/1TIZ76z9lq0SDqArLEEBL9D3V-mILEmNX).

Use a T4 GPU or better, add a Hugging Face read token as the Colab secret `HF_TOKEN`, paste one direct video URL, and choose **Runtime -> Run all**.

## Example evidence

The clearest example is the Adaissah run. Its complete GLB, PNG, CSV, JSON, and ZIP outputs are stored in [Google Drive](https://drive.google.com/drive/folders/1mYRF8jyh3WjBN6N8kyG46DhMjD7qshsF).

The full four-video evidence table and links are in [`validation/REPORT.md`](validation/REPORT.md).

## Current scope

The baseline produces relative 3D reconstruction and relative camera XYZ. It does not yet claim metres, physical speed, latitude, longitude, or altitude.
