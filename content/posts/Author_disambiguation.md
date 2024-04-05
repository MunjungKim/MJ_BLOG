---
author: ["Munjung Kim"]
title: "Author Disambiguation in Scientific Papers"
date: "2024-04-04"
description: "Various author disambiguation methods"
summary: "How researchers disambiguate author names so far"
tags: ["Authorname-disambiguation"]
categories: ["science-of-science", "data", "preprocessing"]
# series: ["Themes Guide"]
ShowToc: true
TocOpen: true
math: true
---

When I try to do a research about the individual scientists' career with large-scale dataset, one of the biggest challenge is data availability since there is no one universally accepted solution for obtaining trustful author identifiers. Different studies focusing on individual careers employ different approaces to achieve accurate author identification as they all use different data sources. Some data sources offer author identifiers, but it is also essential to comprehend the methodologies behind author disambiguation and the reliability of the results obtained to do a research with these datasets. For this reason, I do a survey aiming to explore the diverese approaches adopted by studies or by different data sources. In this post, I classify those approaches by the data sources.




### APS

APS does not provide disambiguated author data. However, the authors of [this paper](https://www-science-org.proxyiub.uits.iu.edu/doi/full/10.1126/science.aaf5239?casa_token=_S6W0TgmfiIAAAAA:cVatiyYCmrDgFuFpcfwBF9-mcjIiqP0SxAFUlShtYdxdXMXHq2KmT3kqI-Krl_XoUwTZTWo7_nz0TQ) tried to do an author disambiguation through a hierachical disambiguation procedure based on meta data in APS dataset. The preceduer is follow:

1)  consider each author of each publication to be a unique one
2) two of authors identified in the previous step are considered to be the same individual if *all* of the following conditions are fulfilled

    i) Last names of the two authors are identical
    ii) initials of the first names and , when available, given names are the same. When the full first names and given names are present for both authors, they have to be identical.
    iii) One of the following is true:
        * the two authors cited each other at leas once
        * the two authors share at leas one co-author
        * the two authors share at least one similar affiliations (which is measured by cosine similarity of tf-idf metrics)

According to the author, accuracy of the disambiguation algorithm evaluated through random 200 pairs papers considered to be written by the same authors and random 200 pairs papers considered to be written by the different authors was not bad. The false positive rate was 2% and false negative rate was 12%. I couldn't find the source code for this method. 

[This paper](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.88.012814) also disambiguated the author name data with the similar method.



### OpenAlex

OpenAlex provides their own author identifiers. It seems like OpenAlex is providing the identifier using the most comprhensive meta dataset. It uses concepts, institutions, citations, coauthor data, and ORCID data if available. According to the description [here](https://github.com/ourresearch/openalex-name-disambiguation/tree/main/V3), OpenAlex used XGBoost to compare these features of authors of each work. It seems like they trained the model with the ORCID dataset. OpenAlex also provides the ORCID of the authors of each work if available. They mentioned that they will release a document with more detials in the future. 


### Web of Science

[This paper]() uses 

### SciSciNet

SciSciNet dataset provided by this [paper](https://www.nature.com/articles/s41597-023-02198-9) also uses MAG author disambiguation method. 

### Other sources

#### Faculty dataset

If you do not need the 
