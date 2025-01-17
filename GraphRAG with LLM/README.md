# GraphRAG with Langchain

This project demonstrates how to use Langchain and GraphQAChain to create a knowledge graph from unstructured text data, and then query it using a large language model (LLM) with integrated graph-based reasoning (GraphRAG).

## Files in this repository

* **`GraphRAG_Langchain_v5.ipynb`:** 
    - Jupyter Notebook containing the core implementation:
        - Knowledge graph creation.
        - Graph-based reasoning.
        - Model testing and evaluation.

* **`graph.gml`:** 
    - Serialized graph data in GML format. 
    - This file stores the extracted knowledge graph in a machine-readable format for later use or sharing.

* **`graph.png`:** 
    - Visual representation of the knowledge graph. 
    - Provides a visual overview of the extracted entities and their relationships, aiding in understanding the graph structure.

* **`pattam_pole.txt`:** 
    - Extracted text content from the Wikipedia page about the Malayalam film *Pattam Pole*. 
    - Serves as the source data for knowledge graph construction.

## Project Overview

1. **Installation:**
    - Install necessary Python libraries using `pip`:
        - Core libraries: `json-repair`, `networkx`, `langchain-core`, `langchain-google-vertexai`, `langchain-experimental`, `langchain-community`, `langchain_google_genai`
        - Additional libraries: `requests`, `beautifulsoup4`, `matplotlib`, `ipywidgets`, `gravis` for data scraping, visualization, and interactive exploration.

2. **Google LLM Model Integration:**
    - Integrate the Gemini 1.5 Flash LLM model using the `langchain_google_genai` package.
    - Obtain and set a Google API key for authenticating with the Google Cloud platform and enabling access to the LLM model.

3. **Text Corpus Creation:**
    - **Data Scraping:** 
        - Fetch the Wikipedia page for the Malayalam film *Pattam Pole* using the `requests` library.
        - Parse the HTML content using `BeautifulSoup4` to extract relevant information and clean the text.
    - **Text Extraction:** 
        - Extract all paragraphs from the parsed HTML.
        - Concatenate the paragraphs to create a single text corpus representing the entire article content.
    - **Data Storage:** 
        - Save the extracted text content to the `pattam_pole.txt` file for future use and reference.

4. **Graph Creation:**
    - **Knowledge Graph Construction:** 
        - Utilize the `GraphIndexCreator` from the Langchain library to process the text data.
        - Identify and extract key entities (e.g., people, places, events) and their relationships (e.g., "directed by," "stars in," "features music by") from the text.
        - Build a directed graph structure using the `networkx` library to represent the extracted knowledge, where nodes represent entities and edges represent relationships between them.
    - **Graph Representation:** 
        - Print the extracted triples (subject-predicate-object) to provide a textual representation of the graph structure and gain insights into the extracted knowledge.

5. **Graph Querying and Comparison:**
    - **Querying:** 
        - Define a function (`compare_answers_llm`) to compare LLM answers with and without context, and with GraphRAG-supported results.
        - Use `GraphQAChain` to query the constructed graph and obtain answers based on the graph structure.
    - **Comparison:** 
        - Evaluate the performance of the LLM with and without context, and compare the results with the GraphRAG-supported answers to assess the impact of graph-based reasoning on answer quality and accuracy.

6. **Graph Serialization and Visualization:**
    - **Serialization:** 
        - Save the constructed graph in GML format (`graph.gml`) for later use, sharing, or further analysis.
    - **Visualization:** 
        - Visualize the graph using various libraries:
            - **Matplotlib:** Create a basic graph visualization for a general overview.
            - **Gravis:** Generate interactive graph visualizations for exploration and analysis.
            - **Plotly:** Create interactive and visually appealing graph visualizations with advanced features for data exploration and presentation.

## Key Components

* **Langchain:** 
    - A powerful framework for building and deploying LLM-powered applications. 
    - Provides tools and utilities for interacting with LLMs, connecting to different data sources, and building complex LLM-based applications.

* **GraphIndexCreator:** 
    - A Langchain tool specifically designed for creating knowledge graphs from text data. 
    - Facilitates the efficient extraction of entities and relationships from unstructured text, enabling the construction of knowledge graphs.

* **GraphQAChain:** 
    - A Langchain chain that leverages the constructed graph to answer questions. 
    - Enables graph-based reasoning by guiding the LLM to utilize the graph structure and relationships to provide more accurate and informative answers.

* **Gemini 1.5 Flash:** 
    - A powerful and advanced Google LLM model. 
    - Provides strong language understanding and generation capabilities, essential for effective graph querying, reasoning, and generating high-quality answers.

This project demonstrates a practical application of knowledge graph technology and how it can enhance LLM performance in question-answering tasks by incorporating graph-based reasoning, leading to more accurate, informative, and reliable answers.
