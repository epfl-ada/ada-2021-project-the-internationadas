# Do People With Different Ideologies Speak Differently?
## Content
- [Do People With Different Ideologies Speak Differently?](#do-people-with-different-ideologies-speak-differently)
  - [Content](#content)
  - [Data story &#8594; here](#data-story--here)
  - [Abstract](#abstract)
  - [Research Questions](#research-questions)
  - [Proposed Datasets](#proposed-datasets)
  - [Methods](#methods)
  - [Setup](#setup)
  - [Proposed Timeline and Team Organization](#proposed-timeline-and-team-organization)
  - [Contributions](#contributions)
## Data story &#8594; [here](https://mxmuc.github.io/do-people-with-different-ideologies-speak-differently/)
## Abstract
One of the most pressing problems facing our society today is animosity across political and social lines. It causes tensions between family and friends, politicians, and the public at large. The acrimony between political groups makes it challenging for people and the government that serves them to solve societal problems. We provide an NLP framework that examines the differences in how ideological subgroups of American politicans express themselves to better understand how a polarization of beliefs can occur in today's media. Using the example of climate change, we aim to provide evidence that the discussion around this phenomenon is highly polarized and that this polarization is motivated by differences between socio-political subgroups. To achieve this, we extract quotations related to climate change that have been uttered by Democrats and Republicans between 2015 and 2020 from the quotebank dataset. We then propose to enrich these quotations with socio-demographic data and cluster the quotation embeddings as a means to identify prominent topics. Measuring within-party and between-party similarity, our work aims to contribute to a deeper understanding of how group divisions manifest themselves in language.
## Research Questions
Our project aims to answer the following questions:
* RQ1: How often do Democrats and Republicans discuss climate change in media?
* RQ2: Is there a difference on how people from different socio-political backgrounds talk?
* RQ3: How could these differences help understand the causes and consequences of media polarization?
* RQ4: What are the most discussed topics among Democrats and Republicans?
* RQ5: Are Democrats really more concerned about climate change than Republicans?
## Proposed Datasets
* `Quotebank`:  Quotation-centric data set of unique quotations with the most likely speaker from 2015-2020
* `WikiData`: Central storage for the structured data of its Wikimedia sister projects including Wikipedia. We use it to enrich the quotations with socio-demographic data of the speakers (e.g., party, gender, occupation)
## Methods
* **Data Loading**
1. Load and filter wikidata Quotebank datasets: the filtering is based on political parties.
2. Merge quotebank and wikidata on the QID.
3. Store merged df for each year in an additional parquet file.
* **Data Preprocessing and Exploration**
1. Drop the quotations with multiple possible Speakers.
2. Drop  quotations with uncertain speakers: for that we set the probability threshold to 0.6.
3. Drop quotations of politicians who switched parties during the time frame.
4. Initial analysis based on political party and gender. 
5. Topic selection: Climate Change. Fix a vocabulary list related to this topic and only leave quotations that contain at least one word from this list.
* **NLP Embeddings and Similarity Comparison** 
6. We decided to use BERT’s pre-trained Sentence Transformer to embed the quotations that contain at least one word from the Vocabulary list (This is a link to an example vocabulary related to climate change [link](https://www.health.state.mn.us/communities/environment/climate/docs/film/vocab_list.pdf)) into numerical arrays.
7. With the embeddings as a vantage point, we use cosine similarity metric to calculate the similarity between the quotations of people with different socio-political background; precisely, similarity for all possible combinations were considered (ie. between and withing parties, and between speakers).
* **Topic Detection and Semantic Analysis**
8. Use of *Latent Dirichlet Allocation (LDA)*, after cleaning and appling tokenizer techniques on quotations, in order to extract topics clusters. To deal with an unbalanced dataset, we decided to use *random oversampling technique*.
9. Use of *Empath* tool to dive deep into a semantic analysis on climate change related sentences among parties
## Setup
To get started, it is necessary to install the `requirements.txt`.
As even our transformed and filtered dataset is relatively large, we did not include it in the repo. Instead, we'd like to ask you to download it from our [Drive](https://drive.google.com/drive/folders/1GcNp2lkck9E2atJnqw2CAvofDEi9H4s5?usp=sharing).
Simply link the drive folder to your own root drive directory. As we committed precompiled Jupyter Notebooks, you can already get an idea of our initial analyses and data handling pipelines by looking at the notebooks.
The overall structure should look like this:

```bash
.
├── requirements.txt
├── README.md
│ 
├── scripts
│   ├── exploratory_data_analysis.ipynb 
│   ├── load_data.ipynb
│   └── nlp_pipeline.ipynb
│ 
```
* `load_data.ipynb` notebook contains functions to load data from a json file (found [here](https://drive.google.com/drive/folders/1R-GVIdxU3jkQb5zU0uG9044Vynh9nYR1?usp=sharing)), and perform initial filtering operations;
* `exploratory_data_analysis.ipynb` notebook contains the entire exploratory analysis: starting from data loading and preprocessing, the focus moves towards the analysis of quotes frequency among different political parties, adding then gender and finally climate change as main topic;
* `nlp_pipeline.ipynb` notebook is the core of our project: focusing on climate change only related quotes, it contains the similarity analysis using bert embedding both at party and speaker level, the topic detection NLP pipeline and the semantic analysis based on lexical categories.
## Proposed Timeline and Team Organization

| Project Milestone     | Date                   | Task                          | Deliverables |
|-----------------------|------------------------|-------------------------------|--------------|
| P2                    | until 2021-11-12       | Finalize data transformations | Merged, cleaned and deduplicated dataset with initial descriptive statistics |
| P2.1                  | until 2021-12-01       | NLP pre-processing of the quotes using BERT | NLP embeddings|
| P2.2                  | until 2021-12-05       | Define topics/concepts (e.g., remembrance, solidarity, ...) and measures to compare subgroups against these topics such as between-group difference and within-group similarity   | list of topics and nearest word stems |
| P2.3                  | until 2021-12-13       | Inferential statistical analysis | Jupyter notebook with plots and textual descriptions|
| P2.4                  | until 2021-12-15       | Create datastory | Web page visualizing our data story|
| P3                    | until 2021-12-17       | Buffer for refinements | final repository containing a well-defined README, a web page visualizing our datastory and different supporting Jupyter notebooks   |

## Contributions
* **Maximilian Pfleger**: research question formulation, climate change data filtering, topic detection and visualization, semantic analysis based on lexical categories, github website setup, data story par. *semantic analysis* and final words;
* **Paolo Celada**: data loading and initial filtering, choiche of similarity metric, sentence cleaning, similarity network and visualizations, data story visualizations set-up, data story par. *quote similarity*, `README` update and produce `requirements.txt`;
* **Yasmine Karoui**: research question formulation, wikidata handling, bert sentence embedding set-up, similarity matrix, data story par. *introduction* and par. *topic detection*;
* **Lorenzo Taschin**: initial data exploration, study of climate change related quotes, quote frequency visualization based on party and topic, similarity-related t-test and confidence intervals, data story par. *climate change in US politics*.