# Do people with different ideologies speak differently? - Analyzing polarization in quotes related to climate change from American politicians
## Content
1. [Abstract](#Abstract)
2. [Research Questions](#Research-Questions)
3. [Proposed Additional Datasets](#Proposed-Additional-Datasets)
4. [Methods](#Methods)
5. [Setup](#Setup)
6. [Proposed Timeline and Team Organization](#Proposed-Timeline-and-Team-Organization)
8. [Questions for TAs](#Questions-for-TAs)
## Abstract
One of the most pressing problems facing our society today is animosity across political and social lines. It causes tensions between family and friends, politicians, and the public at large. The acrimony between political groups makes it challenging for people and the government that serves them to solve societal problems. We provide an NLP framework that examines the differences in how ideological subgroups of American politicans express themselves to better understand how a polarization of beliefs can occur in today's media. Using the example of climate change, we aim to provide evidence that the discussion around this phenomenon is highly polarized and that this polarization is motivated by differences between socio-political subgroups. To achieve this, we extract quotations related to climate change that have been uttered by Democrats and Republicans between 2015 and 2020 from the quotebank dataset. We then propose to enrich these quotations with socio-demographic data and cluster the quotation embeddings as a means to identify prominent topics. Measuring within-topic and between-topic group affiliation, our work aims to contribute to a deeper understanding of how group divisions manifest themselves in language.
## Research Questions
Our project aims to answer the following questions:
* RQ1: How often do Democrats and Republicans dicuss climate change in media?
* RQ2: What is different about how people from different socio-political backgrounds talk?
* RQ3: How could these differences help understand the causes and consequences of media polarization?
* Optional RQ4: Could ideological groups be identified based on particular words they use?
## Proposed Additional Datasets
* `Quotebank`:  Quotation-centric data set of unique quotations with the most likely speaker from 2015-2020
* `WikiData`: Central storage for the structured data of its Wikimedia sister projects including Wikipedia. We use it to enrich the quotations with socio-demographic data of the speakers (e.g., party, gender, occupation)
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

## Proposed Timeline and Team Organization

| Project Milestone     | Date             | Task                          | Deliverables |
|-----------------------|------------------|-------------------------------|--------------|
| P2.1                  | 2021-11-21       | Finalize data transformations | Merged, cleaned and deduplicated dataset with initial descriptive statistics |
| P2.2                  | 2021-12-05       | NLP pre-processing of the quotes using BERT | NLP embeddings|
| P2.3                  | 2021-12-08       | Define topics/concepts (e.g., remembrance, solidarity, ...) and measures to compare subgroups against these topics such as between-group difference and within-group similarity   | |
| P2.4                  | 2021-12-12       | Inferential statistical analysis | Jupyter notebook and textual descriptions|
| P2.5                  | 2021-12-15       | Create datastory | Web page visualizing our data story|
| P3                    | 2021-12-17       | Buffer for refinements | final repository containing a well-defined README, a web page visualizing our datastory and a supporting Jupyter notebook   |

## TA Questions
* Do you think our research questions are well-formulated and feasible?
* If you have some tips or see possible improvements regarding how to better handle data of such size, we are happy to listen to your feedback!


