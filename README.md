# Semantic-Spotter---project

Semantic Spotter Project Submission
1. Background
This project demonstrate "Build a RAG System" in insurance domain using LangChain.

2. Problem Statement
The goal of the project is to build a robust generative search system capable of effectively and accurately answering questions from a bunch of policy documents.


3. System Layers
Reading & Processing PDF Files: We will be using LangChain PyPDFDirectoryLoader to read and process the PDF files from specified directory.

Document Chunking: We will be using LangChain RecursiveCharacterTextSplitter. This text splitter is the recommended one for generic text. It is parameterized by a list of characters. It tries to split on them in order until the chunks are small enough. The default list is ["\n\n", "\n", " ", ""]. This has the effect of trying to keep all paragraphs (and then sentences, and then words) together as long as possible, as those would generically seem to be the strongest semantically related pieces of text..

Generating Embeddings: We will be using OpenAIEmbeddings from LangChain package. The Embeddings class is a class designed for interfacing with text embedding models. LangChain provides support for most of the embedding model providers (OpenAI, Cohere) including sentence transformers library from Hugging Face. Embeddings create a vector representation of a piece of text and supports all the operations such as similarity search, text comparison, sentiment analysis etc. The base Embeddings class in LangChain provides two methods: one for embedding documents and one for embedding a query.

Store Embeddings In ChromaDB: In this section we will store embedding in ChromaDB. This embedding is backed by LangChain CacheBackedEmbeddings

Retrievers: Retrievers provide Easy way to combine documents with language models.A retriever is an interface that returns documents given an unstructured query. It is more general than a vector store. A retriever does not need to be able to store documents, only to return (or retrieve) them. Retriever stores data for it to be queried by a language model. It provides an interface that will return documents based on an unstructured query. Vector stores can be used as the backbone of a retriever, but there are other types of retrievers as well. There are many different types of retrievers, the most widely supported is the VectoreStoreRetriever.

Re-Ranking with a Cross Encoder: Re-ranking the results obtained from the semantic search will sometime significantly improve the relevance of the retrieved results. This is often done by passing the query paired with each of the retrieved responses into a cross-encoder to score the relevance of the response w.r.t. the query. The above retriever is associated with HuggingFaceCrossEncoder with model BAAI/bge-reranker-base

Chains: LangChain provides Chains that can be used to combine multiple components together to create a single, coherent application. For example, we can create a chain that takes user input, formats it with a PromptTemplate, and then passes the formatted response to an LLM. We can build more complex chains by combining multiple chains together, or by combining chains with other components. We are using pulling prompt rlm/rag-promp from langchain hub to use in RAG chain.

4. Prerequisites
Python 3.11+
langchain 0.3.13
Please ensure that you add your OpenAI API key to the empty text file named "OpenAI_API_Key.txt" in order to access the OpenAI API.

5 . Code Running
 full project GitHub link - https://github.com/Rsuhaspavadi/Semantic-Spotter---project.git
 
 code - https://github.com/Rsuhaspavadi/Semantic-Spotter---project/blob/main/semantic-spotter-langchain-notebook%20(1).ipynb