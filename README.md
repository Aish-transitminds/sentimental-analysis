# sentimental-analysis


This project is a Flask-based web application that performs sentiment analysis on text input. It leverages pre-trained models from Hugging Face to classify text as positive, negative, or neutral. The application can process inputs directly from the user, extract content from URLs, or handle uploaded media files.

## Features
- **Sentiment Analysis**: Uses a fine-tuned RoBERTa model ("cardiffnlp/twitter-roberta-base-sentiment-latest") to evaluate the sentiment of the input.
- **Multiple Input Types**:
  - Text input
  - URL extraction (via Goose3)
  - File uploads (media processing)
- **Chunking**: Automatically splits large texts into 510-character chunks to handle long inputs.
- **Sentiment Aggregation**: Aggregates results from all chunks to provide an overall sentiment score.
- **RESTful API**: Returns results as JSON objects for easy integration and API use.

## Technologies Used
- **Flask** - Web framework for Python
- **Hugging Face Transformers** - Pre-trained sentiment analysis model
- **Goose3** - Web content extraction from URLs
- **SciPy** - Softmax computation for model output
- **Werkzeug** - Secure file handling
- **NumPy** - Data aggregation and manipulation

## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/your-repo-name
   cd your-repo-name
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Configure environment variables (e.g., cache directories) in a `.env` file or through system environment variables:
   ```plaintext
   HUGGINGFACE_CACHE_DIR=path/to/cache
   TORCH_CACHE_DIR=path/to/torch_cache
   ```
4. Run the application:
   ```bash
   python views.py
   ```

## How It Works
1. The homepage (`/`) allows users to submit text, URLs, or media files.
2. For text input, the user directly types their content.
3. For URLs, Goose3 extracts the main content of the page.
4. Uploaded files are processed securely and analyzed if they contain extractable text.
5. The input is divided into smaller chunks (if needed) and passed to the sentiment model.
6. The application aggregates sentiment results and returns them in JSON format.

## API Endpoints
- **`/` (GET)**: Renders the home page.
- **`/` (POST)**: Accepts user input and returns sentiment analysis results.

## Example Response
```json
{
  "score_negative": "0.12",
  "score_neutral": "0.55",
  "score_positive": "0.33",
  "prominent_sentiment": "NEUTRAL"
}
```

## Acknowledgements
- [CardiffNLP](https://github.com/cardiffnlp) for the RoBERTa sentiment model.
- [Hugging Face](https://huggingface.co) for their transformer models.
- [Goose3](https://github.com/goose3/goose3) for web content extraction.

