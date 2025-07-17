# NLP_market_analysis

This project provides a Python-based tool for analyzing stock market-related statements. It combines sentiment analysis using the OpenAI GPT-3.5-turbo model with Named Entity Recognition (NER) using spaCy to identify key entities within the text.

## Features

*   **Sentiment Analysis**: Classifies market statements as Positive (bullish), Negative (bearish), or Neutral based on their context in stock market performance.
*   **Named Entity Recognition (NER)**: Extracts entities from the input statements, with a focus on predefined stock market-related entities (e.g., company names, indices, cryptocurrencies).

## Setup and Installation

### Prerequisites

*   Python 3.x
*   An OpenAI API key

### Installation Steps

1.  **Clone the repository (if applicable):**
    ```bash
    git clone <repository_url>
    cd <repository_name>
    ```

2.  **Install required Python packages:**
    ```bash
    pip install openai==0.28 spacy
    python -m spacy download en_core_web_sm
    ```

3.  **Set up your OpenAI API Key:**
    Open the `Market_analysis.ipynb` file and replace `"YOUR_OPENAI_API_KEY"` with your actual OpenAI API key in the following line:
    ```python
    openai.api_key = "YOUR_OPENAI_API_KEY"
    ```

## Usage

To run the analysis, execute the Jupyter Notebook `Market_analysis.ipynb`.

1.  **Open the notebook:**
    ```bash
    jupyter notebook Market_analysis.ipynb
    ```

2.  **Run all cells:**
    Execute all cells in the notebook. The last cell will prompt you for input.

3.  **Provide input:**
    The script will ask you to enter:
    *   **Category**: e.g., `Stock`, `Index`, `Crypto`, `Economy`, `Other`.
    *   **Market Statement**: The text you want to analyze.

    **Example Interaction:**
    ```
    Enter the category (e.g., Stock, Index, Crypto, Economy, Other): Stock
    Enter your market statement related to stock: Seem to go up in the coming month!, excited!!!

    Performing Stock Market Sentiment Analysis...

    Sentiment Analysis Result: Based on the statement "Seem to go up in the coming month!, excited!!!", the sentiment can be classified as Positive (bullish) in the context of stock market performance. The use of "go up" and "excited" indicates optimism and positivity towards potential stock market performance.

    Performing Named Entity Recognition (NER)...

    Identified Market Entities: [('the coming month', 'DATE')]
    ```

## Code Structure

*   **`import openai`, `import spacy`**: Imports necessary libraries.
*   **`!pip install openai==0.28`**: Ensures the correct version of the OpenAI library is installed.
*   **`openai.api_key = "YOUR_OPENAI_API_KEY"`**: Placeholder for your OpenAI API key.
*   **`nlp = spacy.load("en_core_web_sm")`**: Loads the small English language model for spaCy.
*   **`stock_entities`**: A predefined list of stock market-related entities used for additional filtering in NER.
*   **`analyze_sentiment(review, category)` function**:
    *   Takes a `review` (market statement) and `category` as input.
    *   Constructs a prompt for the OpenAI GPT-3.5-turbo model to perform sentiment analysis.
    *   Returns the classified sentiment (Positive, Negative, or Neutral).
*   **`extract_entities(review)` function**:
    *   Takes a `review` (market statement) as input.
    *   Uses spaCy's NER to identify entities.
    *   Filters entities against the `stock_entities` list to prioritize financial terms.
    *   Returns a list of identified entities and their labels.
*   **`main()` function**:
    *   Handles user input for category and market statement.
    *   Calls `analyze_sentiment` and `extract_entities` functions.
    *   Prints the sentiment analysis result and identified entities.
