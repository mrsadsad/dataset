# Multi-Project Function-Level Dataset

This repository provides a **multi-project, function-level dataset** constructed from
multiple open-source software projects.
The dataset is designed for research on **change impact analysis (CIA)**.

Each project is processed independently and follows the same data format.

---

## 1. Dataset Overview

The dataset consists of **function-level triplets** extracted from several open-source projects.
Each triplet contains:

- a **query function**
- a **positive function** (There is a change impact on the query function)
- a **negative function** (There is no impact from changes to the query function)

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

### 3.1 train_data.json

The training dataset is a list of triplets.
Each triplet has the following structure:

```json
{
  "query": "file_path@function_name",
  "pos": "file_path@function_name",
  "neg": "file_path@function_name"
}
query: anchor function

pos: There is a change impact on the query function

neg: There is no impact from changes to the query function


```

### 3.2 test_data.json

The test dataset follows the same format as the training dataset and is used for evaluation.

### 3.3 functionsID_body.json

This file provides a mapping from function identifiers to their corresponding source code.

Example format:

```json
{
  "file_path@function_name": "function source code ..."
}
```

All function identifiers referenced in the training and test datasets
are guaranteed to exist in this file.

## 4. Function Identifier Format

Each function is uniquely identified using the following format:

relative_file_path@function_name
This identifier maps a function to its location and name within a project.

## 5. Data Construction

Functions are extracted at the function level from each project.

All projects use a consistent representation format.

Triplets are constructed to support contrastive learning and code retrieval.

Positive and negative samples are selected based on change impact.

## 6. Project link

**jemalloc**:[jemalloc/jemalloc](https://github.com/jemalloc/jemalloc)

**libbpf**:[libbpf/libbpf: Automated upstream mirror for libbpf stand-alone build.](https://github.com/libbpf/libbpf)

**FFmpegKit**:[arthenica/ffmpeg-kit at v5.1](https://github.com/arthenica/ffmpeg-kit/tree/v5.1)

**librdkafka**:[confluentinc/librdkafka at v2.1.0](https://github.com/confluentinc/librdkafka/tree/v2.1.0)

**TheAlgorithms**:[TheAlgorithms/C: Collection of various algorithms in mathematics, machine learning, computer science, physics, etc implemented in C for educational purposes.](https://github.com/TheAlgorithms/C)

**antiword**:https://fossies.org/linux/misc/old/antiword-0.37.tar.gz