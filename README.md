# Surrogate ADME Multi-Task Predictor

Multi-task graph neural network pretrained on synthetic ADME labels for 270,000+ compounds across 25 endpoints. Predicts permeability (Caco-2, PAMPA, LE-MDCK Papp, MDCK-MDR1 efflux ratio), intrinsic clearance and plasma protein binding in rat, human, mouse, dog, and monkey liver microsomes, human serum albumin/microsomal/brain binding, LogP, LogD, and CYP3A4 time-dependent and CYP3A4/CYP2C9/CYP2D6 reversible inhibition. Supports fine-tuning on experimental data for prospective drug discovery applications.

This model was incorporated on 2026-06-30.


## Information
### Identifiers
- **Ersilia Identifier:** `eos48ue`
- **Slug:** `surrogate-adme`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Property calculation or prediction`
- **Biomedical Area:** `ADMET`
- **Target Organism:** `Any`
- **Tags:** `ADME`, `CYP450`, `Metabolism`, `Permeability`, `LogP`, `LogD`, `Fraction bound`, `Microsomal stability`, `Chemical graph model`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `25`
- **Output Consistency:** `Fixed`
- **Interpretation:** Predicted values for 25 ADME endpoints spanning permeability, clearance, plasma/tissue binding, lipophilicity, and CYP450 inhibition. Most are log-transformed; LogP/LogD are direct. Surrogate-model predictions, not experimental; prospective MAE ~0.23-0.49 log units (Peteani et al., ChemRxiv 2026).

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| le_mdck_v2_logpapp | float | high | Predicted log apparent permeability (LogPapp) in the low-efflux MDCKv2 assay |
| le_mdck_v1_logpapp | float | high | Predicted log apparent permeability (LogPapp) in the low-efflux MDCKv1 assay |
| caco2_logpapp | float | high | Predicted log apparent permeability (LogPapp) in the Caco-2 assay |
| mdck_mdr1_loger | float | high | Predicted log efflux ratio (LogER) in the MDCK-MDR1 assay |
| logpampa | float | high | Predicted log permeability in the parallel artificial membrane permeability assay |
| rat_lm_logclint | float | high | Predicted log intrinsic clearance (LogCLint) in rat liver microsomes |
| human_lm_logclint | float | high | Predicted log intrinsic clearance (LogCLint) in human liver microsomes |
| mouse_lm_logclint | float | high | Predicted log intrinsic clearance (LogCLint) in mouse liver microsomes |
| minipig_lm_logclint | float | high | Predicted log intrinsic clearance (LogCLint) in minipig liver microsomes |
| cyno_lm_logclint | float | high | Predicted log intrinsic clearance (LogCLint) in cynomolgus monkey liver microsomes |

_10 of 25 columns are shown_
### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Replicated`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos48ue.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos48ue.zip)

### Resource Consumption
- **Model Size (Mb):** `856`
- **Environment Size (Mb):** `1816`


### References
- **Source Code**: [https://github.com/chemprop/chemprop](https://github.com/chemprop/chemprop)
- **Publication**: [https://doi.org/10.26434/chemrxiv.15005075/v1](https://doi.org/10.26434/chemrxiv.15005075/v1)
- **Publication Type:** `Preprint`
- **Publication Year:** `2026`
- **Ersilia Contributor:** [arnaucoma24](https://github.com/arnaucoma24)

### License
This package is licensed under a [GPL-3.0](https://github.com/ersilia-os/ersilia/blob/master/LICENSE) license. The model contained within this package is licensed under a [MIT](LICENSE) license.

**Notice**: Ersilia grants access to models _as is_, directly from the original authors, please refer to the original code repository and/or publication if you use the model in your research.


## Use
To use this model locally, you need to have the [Ersilia CLI](https://github.com/ersilia-os/ersilia) installed.
The model can be **fetched** using the following command:
```bash
# fetch model from the Ersilia Model Hub
ersilia fetch eos48ue
```
Then, you can **serve**, **run** and **close** the model as follows:
```bash
# serve the model
ersilia serve eos48ue
# generate an example file
ersilia example -n 3 -f my_input.csv
# run the model
ersilia run -i my_input.csv -o my_output.csv
# close the model
ersilia close
```

## About Ersilia
The [Ersilia Open Source Initiative](https://ersilia.io) is a tech non-profit organization fueling sustainable research in the Global South.
Please [cite](https://github.com/ersilia-os/ersilia/blob/master/CITATION.cff) the Ersilia Model Hub if you've found this model to be useful. Always [let us know](https://github.com/ersilia-os/ersilia/issues) if you experience any issues while trying to run it.
If you want to contribute to our mission, consider [donating](https://www.ersilia.io/donate) to Ersilia!
