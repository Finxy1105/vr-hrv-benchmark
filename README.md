# vr-hrv-benchmark

This repo contains the code for my master's thesis at Stockholm University, where I benchmarked four classification models (Random Forest, SVM, MiniROCKET, and CNN+LSTM) for physiological emotion recognition in VR. The main question was whether complex deep learning models actually outperform simpler ones when tested on data they have never seen before. 
Spoiler: they don't.

## Datasets

You'll need to download the two datasets separately and place them in a `data/` folder.

- **AVDOS-VR** (37 participants): https://www.gnacek.com/affective-video-database-online-study
- **CEAP-360VR** (32 participants): https://github.com/cwi-dis/CEAP-360VR-Dataset

Both datasets use the Empatica E4 wristband for PPG recording, which is what we use here. You don't need the other modalities.

## What the notebook does

Everything lives in one Jupyter notebook. It walks through:

1. PPG signal preprocessing and filtering
2. IBI extraction and HRV feature computation (7 features: 
mean HR, mean IBI, SDNN, RMSSD, pNN50, CV-IBI, IBI range)
3. Within-subject evaluation (5-fold CV)
4. Cross-subject evaluation (LOSO)
5. Cross-dataset evaluation
6. Window length ablation study

## Requirements

```bash
pip install numpy pandas scikit-learn matplotlib seaborn neurokit2 torch sktime
```

Developed with Python 3.9. GPU is only needed if you want to run CNN+LSTM, otherwise everything runs fine on CPU.

## Citation

