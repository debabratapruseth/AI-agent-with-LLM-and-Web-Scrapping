# Web Insights Agent using OpenAI & Web Scraping
This project demonstrates how to build an intelligent Web Insights Agent that uses OpenAI’s GPT-4 and Python-based web scraping to answer questions using content from a specific web page and its linked child pages.

## Designed for beginner Python and AI/ML learners, this project teaches:

•	Function calling with OpenAI (via openai.ChatCompletion)

•	How to scrape and parse web content using BeautifulSoup and requests

•	Context-aware LLM prompting and data chunking

•	Building an autonomous agent that reads and reasons from external webpages

•	Modular Python code structure and clean error handling

## How It Works
•	User Input: The user provides a question and a base URL.

•	Crawling: The agent scrapes the base URL and its internal links.

•	Text Extraction: It extracts and chunks textual data from the HTML content.

•	LLM Reasoning: GPT-4 (or compatible model) is called with the query and relevant text chunks.

•	Response Generation: The agent uses semantic similarity to match relevant chunks and returns an accurate, LLM-powered answer.

## Educational Goals
This hands-on project helps students:

•	Understand how to combine LLMs with classic web scraping

•	Learn basic web crawling principles and ethical scraping

•	Develop context-aware question answering systems

•	Design real-world AI agents using modular Python functions

•	Explore how LLMs reason from external content

## Technologies Used

•	Python 3.x

•	OpenAI API (gpt-4, gpt-3.5-turbo)

•	BeautifulSoup for HTML parsing

•	Google Colab (for easy notebook execution)

## Getting Started

To run this project:

•	Clone the repository or open the notebook in Google Colab.

•	Set your OpenAI API key as an environment variable or secret.

•	Run all cells and try with your own URLs and questions!

## Future Improvements

•	Use chunk limits wisely: If you're using an LLM with small token size (like GPT-3.5-turbo with 4k–8k tokens), limit the number of child pages (e.g., 5–10) to ensure the extracted content fits within the token limit.

•	Summarize before sending: For larger pages, summarize each child page and then send the summaries to the LLM instead of raw content—this is a smart way to manage token constraints.

•	Upgrade for scale: When handling large websites, switch to models with higher token limits (e.g., GPT-4-32k) for more thorough reasoning.

•	Add a Streamlit or Gradio UI for non-technical users

## Limitations & Ethics

Only scrapes internal links from the base domain.

## License

This project is open-source under the MIT License.

## Enhancing the Architecture with RAG + Vector DB

While the current implementation uses basic scraping + LLM prompting, there are scalable and efficient ways to enhance this architecture—especially when dealing with large websites or many linked pages. This is where Retrieval-Augmented Generation (RAG) paired with a Vector Database becomes powerful.

### Why Move to RAG with a Vector Store?

In the next version of this project, we implement a full RAG pipeline using FAISS (or other vector databases like ChromaDB, Pinecone, etc.) to store and query knowledge efficiently.

Here’s why this upgrade is powerful:

1. Scalability
   
•	No longer limited by LLM max token size.

•	Store thousands of chunks from hundreds of web pages.

•	LLM processes only the top-k relevant chunks retrieved at runtime.


3. Performance
   
•	Avoid rescraping on every query—just search the vector DB.

•	Smaller payloads sent to LLM → faster and cheaper responses.

5. Accuracy
   
•	You can chunk based on HTML structure (e.g., headings, sections).

•	Only the most relevant slices (e.g., top-3) are passed to LLM.

•	Improved precision in responses.

7. Maintainability
   
•	Schedule regular scraper runs (e.g., nightly cron jobs) to update content.

•	Your RAG pipeline stays fresh without touching your LLM logic or prompt templates.

