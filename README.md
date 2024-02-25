# TD4CLTabs
TD4CLTabs (**T**able **D**etection for **C**omputational **L**inguistics **Tab**le**s**) is a novel domain-specific table type classification dataset, which contains 15k table images (12k for training and 3k for the test) and their corresponding type labels obtained from [ACL Anthology](https://aclanthology.org/). It is from my master thesis topic supported by TUB and DFKI, namely, `Towards a novel classification of table type in scholarly publications`.

The dataset can be download [here](https://drive.google.com/file/d/1h0r0rqV0UHV8Nv2vVNIWsdlbr7xB0-30/view?usp=drive_link)

## Introduction

The aim of this study was to investigate the effectiveness of taxonomies in classifying
tables within scholarly publications. To
achieve this, two groups of table taxonomies, referred to as **Header-Feature Table Taxonomy (HFTT)** and **Full-Feature Table Taxonomy (FFTT)**, were
developed specifically for academic tables. Furthermore, TD4CLTabs dataset was constructed
using these taxonomies. To evaluate the effectiveness of the proposed taxonomies, a benchmark study was conducted by training ResNet50 and Vit models.

## The structure of dataset directory

```
TD4CLTabs
├── train
    ├── table-img1
    ├── table-img2
    ...
    └── table-imgN
├── test
    ├── table-img1
    ...
    └── table-imgN
├── SciTSRComp
    ├── table-img1
    ...
    └── table-imgN
└── metadata
    ├── labels_metadata.json
    ├── afterAnnotation
        ├── train.csv
        ├── test.csv
        └── scitsrcomp.csv
    ├── HFTT_Baseline_I
        ├── train.csv
        ├── test.csv
        └── scitsrcomp.csv
    ├── HFTT_Baseline_II
        ...
    ├── HFTT_Novel_I
    ├── HFTT_Novel_II
    ├── HFTT_Novel_III
    ├── HFTT_Novel_IV
    ├── HFTT_Baseline_I
    ├── HFTT_Baseline_II
    ├── HFTT_Novel_I
    ├── HFTT_Novel_II
    ├── HFTT_Novel_III
    └── HFTT_Novel_IV
```

The folder **train**, **test**, and **SciTSRComp** contain the table images and folder **metadata** contains the label information for each taxonomy on each dataset.

In **metadata**, *labels_metadata.json* stores all the taxonomy mappings, and for the folders **afterAnnotation**, **HFTT/FFTT_Baseline/Novel_I,II,III,IV** contain only *train.csv*, *test.csv*, and *scitsrcomp.csv* files.

#### *label_metadata.json*

```json
{
    "afterAnnotation": {
        "Header Complexity Type": {
            "0": "Other table",
            "1": "Horizontal Listing",
            ...
            "15": "Vertical Listing"
        },
        "Cell Complexity Type": {
            "1": "Spanning cell",
            ...
        }
    },
    "HFTT_Baseline_I": {
        "0": "Listing",
        "1": "Matrix"
    },
    "HFTT_Baseline_II": {...},
    "HFTT_Novel_I": {...},
        ...
    "HFTT_Novel_IV": {...},
    "FFTT_Baseline_I": {
        "1": "Spanning cell",
        "2": "Hierarchical Row",
        ...
    },
    ...
}
```
