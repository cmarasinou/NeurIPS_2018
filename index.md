---
layout: page
title: NeurIPS 2018
---

All NeurIPS 2018 papers can be found at
https://papers.nips.cc/book/advances-in-neural-information-processing-systems-31-2018

The papers of interest can be found in __refs.bib__ and compiled in [papers.html](./papers.html)

A summary of each paper will follow. The first one is already posted here: [summaries.html](./summaries.html)

## Changing the papers list

- Modify the bibtex file __refs.bib__ appropriately
- Run the following pandoc command

```
$ pandoc --filter=pandoc-citeproc --csl=style.csl --standalone papers.md -o papers.html
```
