# NLP Project: Information Extraction, Summarization & Agentic AI

This repository contains the code and documentation for a multi-part project that demonstrates capabilities in Natural Language Processing (NLP) and AI agent design. The project progresses from basic data preparation to building a sophisticated, real-time research assistant powered by the Gemini API.

This guide is designed for easy execution using **Google Colab**.

---

## 1. Setup & How to Run Each Module (Google Colab)

No local installation is required. The project is divided into two notebooks that can be run directly in your browser.

**Instructions:**

1.  **Open Google Colab:** Go to [colab.research.google.com](https://colab.research.google.com).

2.  **Run Task 1 (Data Preparation & Exploration):**
    * Click on `File` -> `New notebook`.
    * Name the notebook `task1.ipynb`.
    * Copy the code from the `task1.ipynb` file provided and paste it into the first cell.
    * Click the **Play** button (▶️) to run the cell. The code will automatically download the dataset, preprocess it, and display the analysis charts.

3.  **Run Task 2 (Information Extraction & Summarization):**
    * Create another new notebook (`File` -> `New notebook`).
    * Name this one `task2.ipynb`.
    * Copy the code from the `task2.ipynb` file and paste it into the first cell.
    * Click the **Play** button (▶️) to run the cell. This script will install all necessary libraries, download models, and then show examples of information extraction and summarization on sample articles.

---

## 2. Dataset Source and Preprocessing Description

The initial modules of this project use the **News Category Dataset** from Kaggle to develop and test the core NLP functionalities.

* **Source:** [Kaggle News Category Dataset](https://www.kaggle.com/datasets/rmisra/news-category-dataset)
* **Preprocessing Steps Applied:** The notebooks automatically perform the following steps:
    * **Tokenization:** Breaking down text into individual words or tokens.
    * **Lowercasing:** Converting all text to a uniform lowercase.
    * **Stop-word Removal:** Filtering out common words that don't carry significant meaning (e.g., "the", "is", "a").
    * **Lemmatization:** Reducing words to their base or dictionary form (e.g., "running" becomes "run") to consolidate the vocabulary.

---

## 3. Explanation of the Agent Design

The final conceptual piece of this project is a **Real-Time News Research Assistant**, designed around a **Plan-and-Execute** framework. While the full agent is not implemented in the Colab notebooks, its design is the logical conclusion of the project.

### Agent Use-Case & Goal

The agent is designed to help users quickly understand and synthesize information about current events. It can answer complex questions by searching the web, reading articles, and generating a consolidated answer. The agent's primary goal is to provide timely, relevant, and accurate information in response to a user's natural language query.

### Agent Workflow & Architecture

The agent's logic is orchestrated by the **Gemini API** and follows a four-step loop:

1.  **Plan:** When a user provides a query (e.g., "What are the latest developments in AI regulation?"), the agent sends the query and a list of available tools to the Gemini API. Gemini, acting as the reasoning engine, creates a step-by-step plan to answer the query.

2.  **Execute:** The agent's Python code parses the plan and executes the specified tools in the correct sequence. The agent has access to the following tools:
    * `web_searcher`: To find relevant articles on the live web.
    * `Workspace`: To read the full text of an article from a URL.
    * `information_extractor`: To identify key entities like people, places, and organizations.
    * `text_analyzer`: To summarize text or answer a specific question about it.

3.  **Tool Chaining:** The output of one tool is intelligently used as the input for the next. For example, the URLs from `web_searcher` are passed to `Workspace`, and the text from `Workspace` is passed to `text_analyzer`.

4.  **Synthesize:** The evidence gathered from the tool executions is collected and sent back to Gemini in a final prompt. Gemini then synthesizes this information into a single, comprehensive, and easy-to-read answer for the user.

This architecture allows the agent to be both powerful and flexible, capable of tackling a wide range of research tasks by dynamically creating and executing a plan to find the answer.
