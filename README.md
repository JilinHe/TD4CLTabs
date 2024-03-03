# TD4CLTabs
TD4CLTabs (**T**able **D**etection for **C**omputational **L**inguistics **Tab**le**s**) is a novel domain-specific table type classification dataset, which contains 15k table images (12k for training and 3k for the test) and their corresponding type labels obtained from [ACL Anthology](https://aclanthology.org/). It is from my master thesis topic supported by TUB and DFKI, namely, `Towards a novel classification of table type in scholarly publications`.

The dataset can be download [here](https://drive.google.com/file/d/1toiPiinycEcwggbrkb2xZmhDc_CrBRsh/view?usp=sharing)

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
    ├── Baseline_I
        ├── train.csv
        ├── test.csv
        └── scitsrcomp.csv
    ├── Baseline_II
        ...
    ├── HFTT_Novel_I
    ├── HFTT_Novel_II
    ├── HFTT_Novel_III
    ├── HFTT_Novel_IV
    ├── FFTT_Novel_I
    ├── FFTT_Novel_II
    ├── FFTT_Novel_III
    ├── FFTT_Novel_IV
    ├── FFTT_Novel_V
    └── FFTT_Novel_VI
```

The folder **train**, **test**, and **SciTSRComp** contain the table images and folder **metadata** contains the label information for each taxonomy on each dataset.

In **metadata**, *labels_metadata.json* stores all the taxonomy mappings, and for the folders **afterAnnotation**, **Baseline_I,II**, **HFTT_Novel_I,II,III,IV**, and **FFTT_Novel_I,II,III,IV,V,VI** contain only *train.csv*, *test.csv*, and *scitsrcomp.csv* files.

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
    "Baseline_I": {
        "0": "Listing",
        "1": "Matrix",
        "2": "Other table"
    },
    "Baseline_II": {...},
    "HFTT_Novel_I": {...},
        ...
    "HFTT_Novel_IV": {...},
    "FFTT_Novel_I": {
        "1": "Spanning cell",
        "2": "Hierarchical Row",
        ...
    },
    ...
    "FFTT_Novel_VI":{...}
}
```

#### *train.csv*, *test.csv*, *scitsrcomp.csv*

Taking *train.csv* in **HFTT_Novel_I** for example

| |id|HFTT_Novel_I|
|--|--|--|
|0 |2022.acl-demo.1-Table1-1.jpg| 3
1	|2022.acl-demo.1-Table2-1.jpg|	3
2	|2022.acl-demo.1-Table3-1.jpg|	0
3	|2022.acl-demo.10-Table1-1.jpg|	0
4	|2022.acl-demo.11-Table1-1.jpg|	0
...	...	...
10342	|2022.naacl-main.104-Table8-1.jpg|	2
10343	|2022.naacl-main.104-Table9-1.jpg|	2
10344	|2022.naacl-main.105-Table1-1.jpg|	2
10345	|2022.naacl-main.105-Table10-1.jpg|	2
10346	|2022.naacl-main.105-Table11-1.jpg|	0

## The stats of dataset

