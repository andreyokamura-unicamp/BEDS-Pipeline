# BEDS Pipeline

## Introduction
The BERT Error Detection for STPA (BEDS) is a machine-learning Pipeline dedicated to assist the system analyst to perform the first step of the System-Theoretic Process Analysis (STPA) hazard analysis technique.
BEDS was trained using the BERT language model, and specializes in detecting writing errors in sentences that does not follow the guidelines present in the STPA Handbook.

The pipeline has four steps:
1. (Optional) The first step takes an unlabeled sentence and classifies between the Loss, Hazard, and Constraint classes;
2. The second step checks if a sentence is considered either correct or incorrect based on the examples given in the STPA Handbook;
3. The third step checks the category of error present in the incorrect sentences discovered in the previous step;
4. The fourth step uses a sentence similarity model to suggest corrections from a list of verified sentences to the incorrect sentences previously discovered.

## Python Code
Two Python notebooks are available in this repository:
1. **BEDS_Pipeline_Fine_tuning_and_Evaluation** is the code used to manipulate the dataset and train all the ML models of the pipeline;
2. **BEDS_Pipeline_Execution_example** is the functional example of the pipeline.

### How to Use
To experiment with BEDS, you should use **BEDS_Pipeline_Execution_example.ipynb**:
1. Uncomment and install the required libraries;
2. Prepare your input based on the examples given in this repository ("input_example labeled.csv" or "input_example unlabeled.csv");
3. Choose the input type: "labeled" or "unlabeled";
4. Run all lines of code sequentially.
   

## Dataset
This dataset contains textual sentences generated and used during the first step of the ***System-Theoretic Process Analysis*** (STPA) hazard analysis technique, called "defining the purpose of the analysis".
In this step, three security aspects of the system are defined:
- ***Losses*** are something of value which a loss is unacceptable to stakeholders, such as human life, equipment or mission;
- ***System-Level Hazards*** are system states or conditions that, together with a set of worst-case environmental conditions, will lead to a loss;
- ***Sustem-Level Constraints*** are the system's conditions or behaviors that need to be satisfied to prevent hazards.

### Dataset Creation
This dataset was created by extracting sentences found in presentations from the [*Annual MIT STAMP Workshop*](https://psas.scripts.mit.edu/home/).
The presentations are from 2012 to 2023.

### How to Use
The dataset is a ".csv" file.
For Python programming language, the use of Pandas library is recommended:
```python
import pandas as pd
df = pd.read_csv(r'/[PATH]/stpa-dataset.csv')
```

### Dataset Columns
This dataset contains 9 columns that organize the collected data.
1. "sentence": The extracted sentence from the presentation;
2. "label": The corresponding label of the sentence (Loss, Hazard, or Constraint);
3. "validation": Indicates whether the sentence is correct or incorrect;
4. "error": Indicates the type of error in incorrect sentences;
5. "domain": Domain of the presentation;
6. "year": Year of the presentation;
7. "title": Title of the presentation;
8. "url": URL of the presentation;
9. "slide": The number of the slide which the sentence was extracted;


### Class distribution
The sentences extracted are from slides that explicitly show the type of sentence (for example a table explaining which are the system losses and hazards), that automatically represents the corresponding label to be filled in the dataset. However, the presentations containing different amounts of examples lead to an unbalanced dataset.
| Class  | Sentences |
| :---     |        ---: |
| loss  | 291  |
| hazard  | 424  |
| constraint  | 369  |
| Total  | 1084  |


## About the Author
This repository was created by the Computing and Communication Systems graduate student *Andrey Toshiro Okamura*, from the State University of Campinas (UNICAMP)'s School of Technology.
