# 🧠 NeuroLens

**Explainable brain MRI classification with a fine-tuned vision-language model.**

NeuroLens fine-tunes [MedGemma 4B](https://developers.google.com/health-ai-developer-foundations/medgemma) on brain MRI scans to classify tumor type, then explains its prediction with a visual attention map and a short written findings report.

> ⚠️ **Research / portfolio project only.** NeuroLens is not a medical device and must not be used for diagnosis or any clinical decision. MedGemma itself is not clinical-grade without further validation.

## 🚧 Status

Early development - project scaffolding only. Results, metrics, and demo will be added as each stage is completed.

## 🎯 What it will do

1. **Input:** a single brain MRI slice (image).
2. **Classify** into one of four classes: `glioma`, `meningioma`, `pituitary`, `no tumor`.
3. **Explain:** highlight the regions of the scan that most influenced the prediction.
4. **Report:** generate a short, plain-language findings paragraph with the model's confidence and a clear disclaimer.
5. **Demo:** a small web app (Gradio/Streamlit) — upload a scan, get the classification, heatmap, and report.

## 🧩 Approach

| Stage | Plan |
|-------|------|
| Base model | MedGemma 4B (Gemma 3 LLM + SigLIP image encoder, pre-trained on medical data) |
| Fine-tuning | Parameter-efficient fine-tuning (QLoRA) using Hugging Face `transformers` + `peft` |
| Data | Public Kaggle *Brain Tumor MRI* dataset (~7k images, 4 classes) |
| Evaluation | Accuracy, precision, recall, ROC AUC, confusion matrix, per-class failure analysis |
| Explainability | Visual attention overlay on the input scan |
| Compute | Google Colab (free GPU) first; RunPod if more VRAM is needed |

## 🗺 Roadmap

- [ ] Set up environment and load MedGemma
- [ ] Download and clean the dataset; build train/val/test splits
- [ ] Baseline: zero-shot MedGemma accuracy before fine-tuning
- [ ] Fine-tune with QLoRA and track training curves
- [ ] Evaluate (accuracy, ROC AUC, confusion matrix, error analysis)
- [ ] Add explainability heatmaps
- [ ] Add generated findings report
- [ ] Build and deploy the demo app
- [ ] Write up results and limitations

## 📁 Planned structure

```
neurolens/
├── notebooks/      # Colab/Jupyter experiments
├── src/            # data loading, training, evaluation, explainability
├── app/            # demo web app
├── assets/         # figures, sample outputs
└── README.md
```

## 🙏 Acknowledgements

- [MedGemma](https://developers.google.com/health-ai-developer-foundations/medgemma) by Google (subject to its own license and terms of use)
- The public Kaggle Brain Tumor MRI dataset (please follow the dataset's own license and citation requirements)
- DataCamp's *Fine-Tuning MedGemma on a Brain MRI Dataset* tutorial, used as a reference for the general workflow

## 📄 License

MIT for the code in this repository. The MedGemma model weights and the dataset are covered by their own licenses.
