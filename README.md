# **🧠 Knowledge Graph with Personality Modeling**

This repository contains a Python notebook and generated HTML visualizations that demonstrate how to build a **Knowledge Graph (KG)** from unstructured text using **LangChain** and **Google Gemini API**, enriched with **Big Five personality traits** for each identified person entity.

---

## **📘 Overview**

The solution automates the process of:

1. Extracting **entities** and **relationships** from unstructured text.

2. Generating **triplets** (subject–relation–object) via **LLMGraphTransformer**.

3. Modeling **personality traits** (Openness, Conscientiousness, Extraversion, Agreeableness, Neuroticism).

4. Visualizing the final KG interactively using **PyVis**.

This project was designed for an 8-hour assessment task emphasizing independent research, effective LLM use, and reasoning about implementation design.

---

## **🧩 Repository Structure**

`├── KnowledgeGraph_with_Personality_V2.ipynb   # Main notebook (LangChain + Gemini)`  
`├── test.txt                                   # Extract of Albert Einstein's Wikipedia page`  
`├── knowledge_graph.html                       # Graph generated from sample_text (TechInnovate scenario)`  
`├── test_graph.html                            # Graph generated from test.txt (Albert Einstein scenario)`  
`├── Assessment.txt                             # Assessment brief and requirements`  
`├── Copilot Chat.txt                           # Implementation dialogue with Claude (Copilot)`  
`├── Perplexity Chat.md                         # Research and design planning with Perplexity`  
`├── KnowledgeGraph_Assessment_Report.pdf        # Final report generated via GPT-5`  
`└── README.md                                  # (this file)`

---

## **⚙️ Setup Instructions**

### **1\. Environment Setup**

Install required libraries:

pip install langchain langchain-google-genai pyvis networkx python-dotenv

Insert your Gemini API key into the appropriate cell in the notebook (placeholder “xxx” is used)

**Note:** A Google Cloud account with access to the Gemini 1.5/2.x API is required.  
Free-tier rate limits may restrict how much text can be processed at once.

---

## **🚀 Execution Guide**

### **Run the Notebook**

Open `KnowledgeGraph_with_Personality_V2.ipynb` and execute the cells sequentially.

1. **Load text input**

   * The notebook reads either:

     * A hardcoded sample (`sample_text`)

     * A user-provided text file (`test.txt`)

2. **Entity & Relationship Extraction**

   * Uses `LLMGraphTransformer` from LangChain.

   * Generates subject–predicate–object triplets.

3. **Personality Modeling**

   * Prompts Gemini to estimate Big Five scores for each person.

   * Adds trait nodes and weighted edges to the graph.

4. **Visualization**

   * Builds and exports an interactive HTML graph via PyVis.

   * Disables physics for stable node placement.

### **Outputs**

| Input Source | Output File | Description |
| ----- | ----- | ----- |
| `sample_text` (TechInnovate story) | `knowledge_graph.html` | Demonstrates multi-person organization with linked personalities. |
| `test.txt` (Einstein Wikipedia extract) | `test_graph.html` | Illustrates large-scale entity relationships and cross-disciplinary links. |

Open the generated `.html` files in a browser to explore nodes and connections.

---

## **🧪 Dataset Details**

### **1\. Sample Text**

Embedded within the notebook:

John Smith is the CEO of TechInnovate. He's known for his visionary thinking...

This synthetic dataset contains **four fictional professionals** and **organizational relationships**, used for testing entity extraction and personality scoring.

### **2\. Test Data: Albert Einstein Extract**

The file `test.txt` contains a truncated excerpt from the [Wikipedia article on Albert Einstein](https://en.wikipedia.org/wiki/Albert_Einstein).  
 It was used to test model performance on **real historical biographical data**, producing the more complex graph `test_graph.html`.

---

## **📊 Results Summary**

| Scenario | Example Node | Personality Traits | Visualization Notes |
| ----- | ----- | ----- | ----- |
| **TechInnovate** | *John Smith* | O: 0.8, C: 0.7, E: 0.5, A: 0.6, N: 0.3 | Balanced corporate relationship map. |
| **Albert Einstein Extract** | *Albert Einstein* | O: 0.9, C: 0.8, E: 0.3, A: 0.6, N: 0.4 | Rich interconnected academic KG; includes institutions, discoveries, and collaborators. |

Each node includes tooltips showing detailed trait scores and descriptors.  
 Trait edges are labeled with numeric scores (0–1) and rendered with proportional thickness.

---

## **⚠️ Limitations**

* **Gemini API Rate Limits**:  
   The free-tier quota (even for *Gemini 2.5 Flash Lite*) restricts the volume of text processed per minute.  
   Therefore, the full Einstein Wikipedia article could not be parsed in one pass; only a representative extract was used.

* **Trait Consistency**:  
   Personality estimates depend on prompt interpretation and may vary slightly across runs.

* **Graph Clutter**:  
   Large texts can produce dense node clusters, requiring manual zooming for readability.

---

## **🧭 Future Work**

* Integrate **Neo4j** or **Memgraph** for persistent graph storage.

* Add **NER-based normalization** to merge duplicate entities.

* Extend to **GraphRAG** for semantic question answering over the graph.

* Implement **evaluation metrics** (precision/recall) for extracted triples.

---

## **🧠 Credits**

* **LangChain** — Knowledge graph extraction framework.

* **Google Gemini API** — LLM backbone for entity and trait inference.

* **PyVis** — Interactive graph visualization.

* **NetworkX** — Graph data structure handling.