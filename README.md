# Do people with different ideologies speak differently?
## Content
1. [Abstract](#Abstract)
2. [Research Questions](#Research-Questions)
3. [Proposed Additional Datasets](#Proposed-Additional-Datasets)
4. [Methods](#Methods)
5. [Setup](#Setup)
6. [Proposed Timeline](#Proposed-Timeline)
7. [Organization within the Team](#Team-Organization)
8. [Questions for TAs](#Questions-for-TAs)
## Abstract
One of the most pressing problems facing our society today is animosity across political and social lines. It causes tensions between family and friends, co-workers and colleagues, politicians, and the public at large. The acrimony between political groups makes it challenging for people and the government that serves them to solve societal problems. We provide an NLP framework that examines the differences in how ideological subgroups of American politicans express themselves to better understand how a polarization of beliefs can occur in today's media. Our work contributes to a deeper understanding of how group divisions manifest themselves in language and provides computational methods for studying them.
## Research Questions
* RQ1: What are the most common topics discussed by American Politicians in media?
* RQ2: What is different about how people from different socio-political backgrounds talk?
* RQ3: How could these differences help understand the causes and consequences of media polarization?
* RQ4: Could ideological groups be identified based on particular words they use?
## Proposed Additional Datasets
* Quotebank Dataset from 2015-2020
* WikiData 
## Methods

## Setup
To get started, it is necessary to install the `requirements.txt`.
As even our transformed and filtered dataset is relatively large, we did not include it in the repo. Instead, we'd like to ask you to download it from our [Drive](https://drive.google.com/drive/folders/1Pi9XV9RcRePrITCkfHs8njhgbE0YbsIy?usp=sharing).
Simply put the compressed JSON file into the `data` folder. In case you don't want to get your hands dirty and re-execute our pipeline, you can skip the step of manually adding the dataset. As we committed precompiled Jupyter Notebooks, you can already get an idea of our initial analyses and data handling pipelines by looking at the notebooks.
The overall structure should look like this:
```bash
.
├── requirements.txt
├── data
│   └── quotes-enriched-2015-2020-repub-dem.json.bz2
│ 
├── scripts
│   ├── data_loading_transformation.ipynb
│   └── data_analysis.ipynb
│ 
```

## Proposed Timeline

## Team Organization

| Project Milestone     | Date             | Task                          | Deliverables |
|-----------------------|------------------|-------------------------------|--------------|
| P2.1                  | 2021-11-15       |S      | |
| P2.1                  | 2021-11-16       | NLP pre-processing | |
| P2.2                  | 2021-11-17       | Define measures of group affiliation such as between-group difference and within-group similarity   | |
| P2.3                  | 2021-11-18       | | |
| P2.4                  | 2021-11-19       | | |
| P3.                   | 2021-12-17       | | |

## TA Questions


