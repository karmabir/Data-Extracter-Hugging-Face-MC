# HuggingFace Model Scraper
A Python tool for scraping and analyzing popular models from the Hugging Face Hub.
Overview
This script provides a simple way to gather information about machine learning models hosted on HuggingFace, including:
Basic model metadata (author, downloads, likes)
Parameter counts (when available)
Performance metrics across various tasks and datasets
Creation and modification dates
Associated tags
The scraper focuses on popular model families like GPT, LLaMA, BERT, Vision Transformers, and more.
Features
Scrapes models by family name (GPT, LLaMA, Mistral, BERT, etc.)
Sorts results by popularity (downloads)
Extracts parameter counts using multiple methods:
From model card metadata
Through regex pattern matching from README content
Inference from model naming conventions
Collects performance metrics when available
Exports all data to CSV for further analysis
Requirements
python >= 3.6
pandas
requests
beautifulsoup4
tqdm
Installation
Clone this repository or download the script
Install the required dependencies:
pip install pandas requests beautifulsoup4 tqdm
Usage
from huggingface_scraper import HuggingFaceScraper

# Initialize the scraper
scraper = HuggingFaceScraper()

# Scrape up to 100 models
scraper.scrape_models(max_models=100)

# Save to CSV
scraper.save_to_csv("huggingface_models.csv")
Example Output
The resulting CSV will contain columns including:
model_id: Full model identifier (e.g., "facebook/bart-large")
name: Short model name (e.g., "bart-large")
author: Model creator or organization
downloads: Number of downloads
likes: Number of likes/stars
tags: Model tags as a list
created_at: Creation timestamp
last_modified: Last modification timestamp
parameters: Number of parameters (when available)
metric_*: Various performance metrics with task, dataset, and metric type
Customization
You can modify the get_popular_model_families() method to search for different model types:
def get_popular_model_families(self):
    return [
        # Add or remove model families as needed
        "gpt", "llama", "mistral", "falcon",
        "bert", "roberta", 
        "vit", "clip", "resnet", 
        "whisper"
    ]

