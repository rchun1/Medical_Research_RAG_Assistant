# Medical_Research_RAG_Assistant
This project utilizes LLMs (Large Language Model) and RAG (Retrieval-Augmented Generation) to create a helpful medical research assistant that guides students in writing research papers.

The LLM used is llama3 and the RAG chain used is the Langchain QA chain. [^1]

## Usage
On first use of the tool, a user will provide a topic sentence to the first RAG chain to help write the outline for the essay.
On second pass, another RAG chain will use the outline produced from the previous RAG chain to produce a medical essay based on the given topic. To do this, copy and paste outline from first chain and put it into query of second chain.

IMPORTANT NOTE: This project was run in Colab using TPU v2 to support RAM requirements for the RAG chain. Make sure RAM memory is capable of handling requirements(roughly 40 GB of RAM). 

## Loading Data
The assistant utilizes two supplemental vector databases, one for background information and another for bibliographic references.
Documents to load those databases are downloaded from [PubMed](https://pubmed.ncbi.nlm.nih.gov/)

A download script is provided [pubmed_download.py](https://github.com/rchun1/Medical_Research_RAG_Assistant/blob/main/pubmed_download.py) to retrieve the documents and save them in the **data** subdirectory.

Example script execution to download 2023 documents from PubMed:
```
python download_pubmed.py --start  "2023/01/01" --end "2023/12/31"
```

Letters, review articles, and conference abstracts are saved in **pubmed_background.json**

Journal article and clinical trials are saved in **pubmed_reference.json**

## LLMs

The LLM  used is llama3 with the correct huggingface directory

## RAG Chains

For quick feedback and prototyping, we've saved the execution in jupyter notebooks.

## References

[^1]:[https://api.python.langchain.com/en/latest/chains/langchain.chains.retrieval_qa.base.RetrievalQA.html#langchain.chains.retrieval_qa.base.RetrievalQA(https://api.python.langchain.com/en/latest/chains/langchain.chains.retrieval_qa.base.RetrievalQA.html#langchain.chains.retrieval_qa.base.RetrievalQA)

