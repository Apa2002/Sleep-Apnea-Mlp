# Sleep-Apnea-MLP

Independent implementation **and** extension of the method described in the article below, plus a custom C# GUI and extra statistical analysis.

## Reference (Original Method)

Kohzadi, Zeinab, Reza Safdari, and Khosro Sadeghniiat Haghighi. (2020).
*Determination of sleep apnea severity using multi-layer perceptron neural network*.
**Sleep Medicine Research**, 11(2), 70–76.

---

## Repository Structure

```text
Sleep-Apnea-MLP/
│
├── README.md
├── LICENSE
├── requirements.txt
│
├── Original_Method/                # Reproduction of the paper's MLP approach
│   ├── train_model.py
│   ├── predict_apnea.py
│   ├── model.h5
│   └── screenshots/
│
├── Improved_Method/                # Work beyond the paper
│   ├── Statistical_Data_Analysis(Part1)/
│   ├── Feature_Selection(Part2)/
│   ├── Model_Training_Metrics(Part3)/
│   └── results/
│
└── GUI_CSharp/                     # Windows Forms GUI (independent contribution)
    ├── WindowsFormsApplication7/
    └── screenshots/
```

---

## Data Source

Kaggle dataset: **Sleep Health and Lifestyle Dataset**
[https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset](https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset)

* 400 rows × 13 columns
* Variables: gender, age, occupation, sleep duration/quality, physical activity, stress level, BMI category, blood pressure, heart rate, daily steps, sleep disorder (None / Insomnia / Sleep Apnea).

> **Note:** The dataset author states the data is **synthetic** and created for illustrative purposes.

---

## Components

### 1) Original Method (Article Implementation)

Reproduces the paper’s MLP (8–10–3–1, sigmoid) with 10-fold validation and metrics.

### 2) Improved Method (Extended Work)

* **Statistical & data analysis** (normality checks, chi-square, Mann–Whitney, correlation).
* **Feature selection** via **Wrapper** + correlation pruning (e.g., Φ and biserial).
* **Training & metrics** with additional experiments (Adam/ReLU variant, k-fold, reports).

### 3) C# GUI (Windows Forms)

Interactive prediction app that calls the saved Python model (`model.h5`) and shows results to end users.

> The original article **did not** include a GUI; this component is independently designed and implemented here.

---

## Results (Summary)

| Method                    | Accuracy (%) | Sensitivity (%) | Specificity (%) |
| ------------------------- | ------------ | --------------- | --------------- |
| **Improved (this repo)**  | **85.84**    | 46.60           | **97.60**       |
| Implementation (baseline) | 56.97        | 40.00           | 59.12           |
| Paper (reported)          | 94.50        | 86.10           | 95.30           |

> The improved pipeline substantially boosts **accuracy** and **specificity** versus a basic implementation on this dataset.
> Sensitivity still has room for improvement and is a focus for future work.

---

## Installation & Usage

### 1) Clone & install

```bash
git clone https://github.com/your-username/Sleep-Apnea-MLP.git
cd Sleep-Apnea-MLP
pip install -r requirements.txt
```

### 2) Train

```bash
python Original_Method/train_model.py
```

### 3) Predict

```bash
python Original_Method/predict_apnea.py
```

### 4) Run the GUI (C#)

Open `GUI_CSharp/WindowsFormsApplication7/WindowsFormsApplication7.sln` in **Visual Studio**, then build and run.

---

## Suggested `requirements.txt`

```text
tensorflow>=2.12
keras>=2.12
numpy
pandas
scikit-learn
scipy
matplotlib
```

(Adjust versions to your environment.)

---

## Notes for Reproducibility

* The Kaggle dataset is synthetic and differs from the paper’s clinical dataset; metric gaps vs. the article are expected.
* Wrapper feature selection tries many combinations; running it can be time-consuming—consider using Google Colab.

---

## License

Code in this repository is released under **CC BY-NC 4.0**.

* Non-commercial use, sharing, and adaptation are allowed **with attribution**.
* Commercial use requires explicit permission.

[https://creativecommons.org/licenses/by-nc/4.0](https://creativecommons.org/licenses/by-nc/4.0)

---

## Disclaimer

I am **not** an author of the referenced article or the Kaggle dataset.
This repository contains **my own implementation** of the described method, **an independently developed GUI**, and **additional statistical analyses** using the synthetic dataset.
