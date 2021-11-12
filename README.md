# Do People With Different Ideologies Speak Differently?
## Content
1. [Abstract](#Abstract)
2. [Research Questions](#Research-Questions)
3. [Proposed Datasets](#Proposed-Datasets)
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
## Proposed Datasets
* `Quotebank`:  Quotation-centric data set of unique quotations with the most likely speaker from 2015-2020
* `WikiData`: Central storage for the structured data of its Wikimedia sister projects including Wikipedia. We use it to enrich the quotations with socio-demographic data of the speakers (e.g., party, gender, occupation)
## Methods
* **Data Loading**
1. load and filter wikidata Quotebank datasets: The filtering is based on polytical parties.
2. Merge quotebank and wikidata on the QID.
3. Store merged df for each year in an additional parquet file.
* **Data Preprocessing and Exploration**
1. Drop the quotations with multiple possible Speakers.
2. Drop  quotations with uncertain speakers: For that we set the probability threshold to 0.6.
3. Drop quotations of politicians who switched parties during the time frame.
4. Initial analysis based on political party and gender. 
5. Initial topic selection: * Climate Change. Fixe a vocabulary list related to this topic and only leave Quotations that contain at least one word from this list.
* **NLP Embeddings and Similarity Comparison** 
6. We decided to use BERT’s pre-trained Sentence Transformer to embed the Quotations that contain at least one word from the Vocabulary list (This is a link to an example vocabulary related to climate change [link](https://www.health.state.mn.us/communities/environment/climate/docs/film/vocab_list.pdf)) into numerical arrays. 
7. With the embeddings as a vantage point, we will use similarity metrics such as the cosine similarity or the Euclidean-distance to calculate the similarity between the quotations of people with different political background.
## Setup
To get started, it is necessary to install the `requirements.txt`.
As even our transformed and filtered dataset is relatively large, we did not include it in the repo. Instead, we'd like to ask you to download it from our [Drive](https://drive.google.com/drive/folders/1GcNp2lkck9E2atJnqw2CAvofDEi9H4s5?usp=sharing).
Simply link the drive folder to your own root driver directory. As we committed precompiled Jupyter Notebooks, you can already get an idea of our initial analyses and data handling pipelines by looking at the notebooks.
The overall structure should look like this:

```bash
.
├── requirements.txt
├── README.md
│ 
├── scripts
│   ├── load_data.ipynb
│   └── data_exploration.ipynb
│ 
```
The `load_data.ipynb` notebook contains functions to load data from a json file (found [here](https://drive.google.com/drive/folders/1R-GVIdxU3jkQb5zU0uG9044Vynh9nYR1?usp=sharing)), and perform initial filtering operations).<br>
The *load_exploration.ipynb* notebook instead contains a function to load, merge and perform additional filtering operation on preprocessed data for different years, together with the initial analysis with as target our initial question.
## Proposed Timeline and Team Organization

| Project Milestone     | Date                   | Task                          | Deliverables |
|-----------------------|------------------------|-------------------------------|--------------|
| P2.1                  | until 2021-11-21       | Finalize data transformations | Merged, cleaned and deduplicated dataset with initial descriptive statistics |
| P2.2                  | until 2021-12-05       | NLP pre-processing of the quotes using BERT | NLP embeddings|
| P2.3                  | until 2021-12-08       | Define topics/concepts (e.g., remembrance, solidarity, ...) and measures to compare subgroups against these topics such as between-group difference and within-group similarity   | list of topics and nearest word stems |
| P2.4                  | until 2021-12-12       | Inferential statistical analysis | Jupyter notebook with plots and textual descriptions|
| P2.5                  | until 2021-12-15       | Create datastory | Web page visualizing our data story|
| P3                    | until 2021-12-17       | Buffer for refinements | final repository containing a well-defined README, a web page visualizing our datastory and a supporting Jupyter notebook   |

## TA Questions
* Do you think our research questions are well-formulated and feasible?
* We have 72577 quotations related to climate change. Do you think these are enough to answer our research questions? 
* If you have better topic suggestions, we would be happy to take your advice!
* If you have some tips or see possible improvements regarding how to better handle data of such size, we are happy to listen to your feedback!


