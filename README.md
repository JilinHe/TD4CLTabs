# TD4CLTabs

<!-- TD4CLTabs (**T**able **D**etection for **C**omputational **L**inguistics **Tab**le**s**) is a novel domain-specific table type classification dataset, which contains 13k table images (10k for training and 3k for the test) and their corresponding type labels obtained from [ACL Anthology](https://aclanthology.org/). -->

This repository stores the code implementation for the following paper:
 
He, J.,  Borisova, E., & Rehm, G. 2024. Towards a Novel Classification of Table Types in Scholarly Publications. Accepted to the Natural Scientific Language Processing and Research Knowledge Graphs Workshop (NSLP 2024).

The aim of the paper was to investigate the effectiveness of taxonomies in classifying
tables within scholarly publications. To
achieve this, two groups of table taxonomies, referred to as **Header-Feature Table Taxonomy (HFTT)** and **Full-Feature Table Taxonomy (FFTT)**, were
developed specifically for academic tables. Furthermore, TD4CLTabs dataset was constructed
using these taxonomies. To evaluate the effectiveness of the proposed taxonomies, a benchmark study was conducted by training ResNet50 and Vit models. 

Codes can be found in two files *resnet50_model.ipynb* and *vit_model.ipynb*. The dataset can be found and downloaded on [zenodo](https://zenodo.org/records/10972922). 

<!-- 
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

Below is *train.csv* in **FFTT_Novel_V**

| |id|FFTT_Novel_V|
|--|--|--|
|0 |2022.acl-demo.1-Table1-1.jpg| 15
1	|2022.acl-demo.1-Table2-1.jpg|	15
2	|2022.acl-demo.1-Table3-1.jpg|	1 7
3	|2022.acl-demo.10-Table1-1.jpg|	3 7
4	|2022.acl-demo.11-Table1-1.jpg|	7
...	...	...
7682	|2022.findings-acl.67-Table2-1.jpg|	1 3 8
... ... ...
10342	|2022.naacl-main.104-Table8-1.jpg|	9
10343	|2022.naacl-main.104-Table9-1.jpg|	9
10344	|2022.naacl-main.105-Table1-1.jpg|	9
10345	|2022.naacl-main.105-Table10-1.jpg|	9
10346	|2022.naacl-main.105-Table11-1.jpg|	1 7

## The staticstic of dataset

|Type\\# images |training set| test test | SciTSRComp dataset|
|--|--|--|--|
|Total|10,347| 2,954 | 716|
|**Baseline_I**|
|Listing|4,404|1,345|229|
|Matrix|5,891|1,567|469|
|Other|52|42|18|
|**Baseline_II**|
|Matrix|5,891|1,567|469|
|Horizontal Listing|3,649|1,164|207|
|Vertical Listing|498|105|18|
|Enumeration|257|76|4|
|Other|52|42|18|
|**HFTT_Novel_I**|
|Listing|4,011|1,260|127|
|Matrix|3,048|759|72|
|Hierarchical Matrix|2,843|808|397|
|Hierarchical Listing|393|85|102|
|Other table|52|42|18|
|**HFTT_Novel_II**|
|Listing|4,011|1,260|127|
|Matrix|3,048|759|72|
|Type H1 Matrix|1,813|500|318|
|Type H2 Matrix|543|158|27|
|Type H3 Matrix|487|150|52|
|Hierarchical Listing|393|85|102|
|Other table|52|42|18|
|**HFTT_Novel_III**|
|Listing|4,011|1,260|127|
|Pseudo Matrix|2,133|410|53|
|Type H1 Pseudo Matrix|1,384|373|180|
|Matrix|915|349|19|
|Type H1 Matrix|429|127|138|
|Hierarchical Listing|393|85|102|
|Type H3 Pseudo Matrix|389|127|36|
|Type H2 Pseudo Matrix|357|127|19|
|Type H2 Matrix|186|31|8|
|Type H3 Matrix|98|23|16|
|Other table|52|42|18|
|**HFTT_Novel_IV**|
|Pseudo Matrix|4,263|1,037|288|
|Listing|4,011|1,260|127|
|Matrix|1,628|530|181|
|Hierarchical Listing|393|85|102|
|Other table|52|42|18| -->

## Citation

```
@inproceedings{he-etal-2024,
  author = {He, Jilin and Borisova, Ekaterina and Rehm, Georg},
  title = {Towards a Novel Classification of Table Types in Scholarly Publications},
  booktitle = {Proceedings of the 1st Natural Scientific Language Processing and Research Knowledge Graphs Workshop (NSLP)},
  year = {2024},
  comment = {Accepted to NSLP 2024. Link will be provided when available.}
}
```
