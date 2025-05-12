# Zero-shot and Few-Shot Chest X-Ray Classification

This repository supports zero-shot and few-shot classification for both common and rare chest diseases using large-scale public datasets and CLIP-based models.

Rare Diseases often lack high quality annotated datasets. This makes it challenging not only for doctors and radiologists, but also for researchers in divising ways to conduct proper diagnosis. Zero-shot and Few-shot learning techniques paired with the right models offer hope and support for millions of patients worldwide as a solution to this dilemna. 

---

## Datasets

### Common Diseases: NIH ChestX-ray14

* **Link**: [NIH ChestX-ray14 on Kaggle](https://www.kaggle.com/datasets/nih-chest-xrays/data)
* **Description**: A widely used dataset from the National Institutes of Health (NIH) containing over 100,000 frontal-view chest X-ray images from more than 30,000 unique patients.
* **Labels**: 14 common thoracic disease labels such as Pneumonia, Effusion, Infiltration, Nodule, Mass, etc. are present in the dataset.
* **Purpose**: Serves as the primary dataset for the common disease classification pipeline.

### Rare Diseases: MIMIC-CXR-JPG

* **Link**: [MIMIC-CXR-JPG on PhysioNet](https://physionet.org/content/mimic-cxr-jpg/2.0.0/)
* **Description**: A large, de-identified dataset of chest X-rays associated with radiology reports collected from the Beth Israel Deaconess Medical Center.
* **Format**: JPEG images extracted from the DICOM format, paired with free-text reports.
* **Usage in This Project**: I extract rare disease instances from the reports and construct a smaller, task-specific subset for few-shot learning and zero-shot evaluation.
* **Note**: There are certain privacy agreements and steps that must be taken before accessing this dataset. Visit PhysioNet or the dataset for more details. Without these necessary steps the code for creating a mini-dataset stored under RD will not work, nor can the images be accessed. 

---

## GPU & Cloud Resources

This project leverages [Kaggle Notebooks](https://www.kaggle.com/code) with GPU acceleration (Tesla P100, T4) to facilitate fast training and inference. All experiments are reproducible via provided code and notebooks.

---

## Requirements

Install the required dependencies using the following command:

```bash
pip install git+https://github.com/openai/CLIP.git scikit-learn matplotlib
```

The following libraries are also used in the codebase:

* `torch`, `torchvision` (for deep learning)
* `numpy`, `pandas`, `os`, `random`
* `PIL` (image loading)
* `tqdm` (progress bars)
* `clip` (OpenAI CLIP model)

I recommend using Python 3.8+ and a CUDA-enabled GPU for best performance.

---

## Project Structure

```
zero-shot-chest-xray/
├── CD/                      # Code for common disease tasks (NIH)
│   ├── CommonDisease.ipynb
│   └── ...
├── RD/                     # Code for rare disease tasks + data creation (MIMIC)
│   ├── RareDisease.ipynb
│   └── ...
├── LICENSE
├── README.md
├── RD+CD.ipynb
├── requirements.txt
```

> Full evaluation code is combined and stored in RD+CD.ipynb for quick reference. 

---

## Citation

If you use this code or datasets in your research, please cite the respective sources:

**NIH Chest X-ray Dataset**: Wang et al., "ChestX-ray8: Hospital-scale Chest X-ray Database and Benchmarks on Weakly-Supervised Classification and Localization of Common Thorax Diseases" (CVPR 2017)

**MIMIC-CXR-JPG**: Johnson et al., "MIMIC-CXR: A large publicly available database of labeled chest radiographs" (arXiv 2019)

**CLIP**: Radford et al., "Learning Transferable Visual Models From Natural Language Supervision" (ICML 2021)


---

## License

MIT License. See `LICENSE` for details.
