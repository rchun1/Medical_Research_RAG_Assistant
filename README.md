# Medical_Research_RAG_Assistant
This project utilizes LLMs (Large Language Model) and RAG (Retrieval-Augmented Generation) to create a helpful medical research assistant that guides students in writing research papers.

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

[^1]: [https://docs.llamaindex.ai/en/stable/understanding/indexing/indexing/](https://docs.llamaindex.ai/en/stable/understanding/indexing/indexing/)

[^2]: [https://docs.llamaindex.ai/en/stable/examples/vector_stores/ChromaIndexDemo/](https://docs.llamaindex.ai/en/stable/examples/vector_stores/ChromaIndexDemo/)

[^3]: [https://www.llamaindex.ai/blog/using-llamaindex-and-llamafile-to-build-a-local-private-research-assistant](https://www.llamaindex.ai/blog/using-llamaindex-and-llamafile-to-build-a-local-private-research-assistant)

[^4]: [https://docs.llamaindex.ai/en/stable/getting_started/starter_tools/rag_cli/](https://docs.llamaindex.ai/en/stable/getting_started/starter_tools/rag_cli/)

[^5]: [https://medium.com/the-ai-forum/create-a-blog-writer-multi-agent-system-using-crewai-and-ollama-f47654a5e1cd](https://medium.com/the-ai-forum/create-a-blog-writer-multi-agent-system-using-crewai-and-ollama-f47654a5e1cd)

[^6]: [https://docs.llamaindex.ai/en/latest/examples/chat_engine/chat_engine_context/](https://docs.llamaindex.ai/en/latest/examples/chat_engine/chat_engine_context/)

[^7]: [https://llamahub.ai/l/readers/llama-index-readers-json](https://llamahub.ai/l/readers/llama-index-readers-json)

[^8]: [https://docs.llamaindex.ai/en/stable/examples/query_engine/json_query_engine/](https://docs.llamaindex.ai/en/stable/examples/query_engine/json_query_engine/)

[^9]: [https://docs.llamaindex.ai/en/stable/module_guides/deploying/agents/usage_pattern/#query-engine-tools](https://docs.llamaindex.ai/en/stable/module_guides/deploying/agents/usage_pattern/#query-engine-tools)
