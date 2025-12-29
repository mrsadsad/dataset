# Multi-Project Function-Level Dataset

This repository provides a **multi-project, function-level dataset** constructed from
multiple open-source software projects.
The dataset is designed for research on **code representation learning**, **code search**,
and **change impact analysis (CIA)**.

Each project is processed independently and follows the same data format.

---

## 1. Dataset Overview

The dataset consists of **function-level triplets** extracted from several open-source projects.
Each triplet contains:

- a **query function**
- a **positive function** (semantically related)
- a **negative function** (semantically unrelated)

Functions are identified by their source file paths and function names.
The corresponding function bodies are stored separately.

The dataset supports training and evaluation for contrastive and retrieval-based tasks.

---

## 2. Repository Structure

Each project in the dataset is stored using the same file structure.
An example project (**Antiword**) is shown below:

antiword_train_data.json
antiword_test_data.json
antiword_functionsID_body.json


Other projects in the repository follow the same naming and format conventions.

---

## 3. Files Description (Per Project)

For each project, the following three files are provided.

### 3.1 *_train_data.json

The training dataset is a list of triplets.
Each triplet has the following structure:

```json
{
  "query": "file_path@function_name",
  "pos": "file_path@function_name",
  "neg": "file_path@function_name"
}
query: anchor function

pos: semantically related (positive) function

neg: semantically unrelated (negative) function

3.2 *_test_data.json
The test dataset follows the same format as the training dataset and is used for evaluation.

3.3 *_functionsID_body.json
This file provides a mapping from function identifiers to their corresponding source code.

Example format:

{
  "file_path@function_name": "function source code ..."
}
All function identifiers referenced in the training and test datasets
are guaranteed to exist in this file.

4. Function Identifier Format
Each function is uniquely identified using the following format:

relative_file_path@function_name
This identifier maps a function to its location and name within a project.

5. Data Construction
Functions are extracted at the function level from each project.

All projects use a consistent representation format.

Triplets are constructed to support contrastive learning and code retrieval.

Positive and negative samples are selected based on semantic relevance.

6. Dataset Characteristics
Programming language: C

Granularity: Function-level

Number of projects: 6

Each project contains:

a training set

a test set

a function body mapping file

Detailed statistics (e.g., number of functions and triplets per project)
can be obtained by parsing the JSON files.

7. Usage Example
Below is an example of loading a single project dataset using Python:

import json

with open("antiword_train_data.json", "r") as f:
    train_data = json.load(f)

with open("antiword_functionsID_body.json", "r") as f:
    function_bodies = json.load(f)

sample = train_data[0]
query_body = function_bodies[sample["query"]]
The same code applies to all other projects in the dataset.

8. Intended Use
This dataset can be used for:

Code representation learning

Code similarity and retrieval

Contrastive learning on source code

Function-level change impact analysis

Cross-project evaluation

9. License
This dataset is released for academic research purposes only.
Please cite the corresponding paper if you use this dataset in your research.
