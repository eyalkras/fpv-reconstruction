# FPV Reconstruction - Review Package

This repository contains the finished relative-reconstruction baseline and its compact supporting evidence.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/eyalkras/fpv-reconstruction/blob/main/notebooks/FPV_Reconstruction.ipynb)

## Open these in order

Use the **Download** links below. GitHub's inline PDF preview can show an error
even when a PDF is valid; these links open the original verified files directly.

1. [Download the project guide](https://github.com/eyalkras/fpv-reconstruction/raw/refs/heads/main/docs/FPV_Project_Guide.pdf) - concise project explanation.
2. [Download the example run](https://github.com/eyalkras/fpv-reconstruction/raw/refs/heads/main/docs/FPV_Example_Run.pdf) - visual walkthrough from a video URL to the final outputs.
3. [Download the validation summary](https://github.com/eyalkras/fpv-reconstruction/raw/refs/heads/main/docs/FPV_Validation_Summary.pdf) - one-page evidence summary across four representative videos.
4. [`notebooks/FPV_Reconstruction.ipynb`](notebooks/FPV_Reconstruction.ipynb) - clean canonical Colab notebook.

## Live notebook

Use the **Open in Colab** button above. It opens the clean, verified notebook directly from this public GitHub repository.

Before the first run:

1. [Accept the VGGT-Omega access conditions](https://huggingface.co/facebook/VGGT-Omega).
2. [Create a Hugging Face token](https://huggingface.co/settings/tokens) with **read** access.
3. In Colab, select a **T4 GPU** or better.
4. Open **Secrets** using the key icon, add the token with the exact name `HF_TOKEN`, and enable **Notebook access**. Never paste the token into the notebook code.
5. Paste one direct video URL and choose **Runtime -> Run all**.

The GitHub repository and canonical notebook are public. Saved example outputs
remain in Google Drive and may require separate access.

## Example evidence

The clearest example is the Adaissah run. Its complete GLB, PNG, CSV, JSON, and ZIP outputs are stored in [Google Drive](https://drive.google.com/drive/folders/1mYRF8jyh3WjBN6N8kyG46DhMjD7qshsF).

The full four-video evidence table and links are in [`validation/REPORT.md`](validation/REPORT.md).

## Current scope

The baseline produces relative 3D reconstruction and relative camera XYZ. It does not yet claim metres, physical speed, latitude, longitude, or altitude.
