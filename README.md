
# 📰 Website Summarizer using Ollama + BeautifulSoup

This project is a simple yet powerful tool that **scrapes a website, cleans unnecessary elements, and generates a concise AI-powered summary** using [Ollama](https://ollama.ai/) and an LLM model (e.g., `llama3.2`).

It is especially useful for quickly digesting **news articles, blog posts, and web content** without distractions like ads, navigation menus, or scripts.

---

## 🚀 Features

* Scrapes any given webpage using `requests` and `BeautifulSoup`.
* Extracts **page title** and **clean readable text** (removes scripts, styles, images, etc.).
* Generates **short, markdown-formatted summaries** using an Ollama-powered LLM.
* Includes utility functions for Jupyter Notebook integration (`IPython.display.Markdown`).
* Modular design:

  * `Website` class → handles scraping & cleaning.
  * `user_prompt_for()` → builds user instructions for the AI.
  * `messages_for()` → packages system & user prompts together.
  * `summarize()` → calls Ollama to get the summary.
  * `display_summary()` → pretty display in Jupyter notebooks.

---

## 🛠️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/website-summarizer.git
cd website-summarizer
```

### 2. Install Dependencies

Make sure you have **Python 3.9+** installed.

```bash
pip install -r requirements.txt
```

**requirements.txt**

```txt
requests
beautifulsoup4
python-dotenv
ipython
ollama
```

### 3. Install Ollama

Follow instructions from [Ollama’s official site](https://ollama.ai/download) to install it on your system.

Then pull the model (example with `llama3.2`):

```bash
ollama pull llama3.2
```

---

## ⚡ Usage

### Example Script

```python
from summarizer import display_summary

url = "https://www.moneycontrol.com/news/business/markets/trade-setup-for-september-12-top-15-things-to-know-before-the-opening-bells-13540563.html"
display_summary(url)
```

This will:

1. Scrape the webpage.
2. Extract clean text.
3. Generate a **concise markdown summary** via Ollama.

---

## 📂 Project Structure

```
website-summarizer/
│── summarizer.py        # Core logic (Website class, scraping, summarization)
│── requirements.txt     # Python dependencies
│── README.md            # Documentation (this file)
│── .env                 # Optional: store API keys or config variables
```

---

## 🔑 Key Concepts

### `Website` class

* Fetches webpage with **browser-like headers** to avoid being blocked.
* Parses HTML with BeautifulSoup.
* Removes irrelevant elements (`script`, `style`, `img`, `input`).
* Extracts clean text and page title.

### Prompt Functions

* `system_prompt`: Sets context → “You are an assistant that summarizes websites…”
* `user_prompt_for(website)`: Builds the user’s request with extracted text.
* `messages_for(website)`: Packages both system + user prompts for Ollama.

### Summarization

* `summarize(url)`: Gets cleaned text → sends to Ollama → returns summary.
* `display_summary(url)`: Pretty-prints summary inside Jupyter Notebooks.

---

## 📒 Example Output

### Input URL

`https://www.moneycontrol.com/news/business/markets/trade-setup-for-september-12-top-15-things-to-know-before-the-opening-bells-13540563.html`

### Output Summary (Markdown)

```markdown
### 📊 Trade Setup for September 12

- Indian markets are expected to open on a cautious note due to mixed global cues.  
- Nifty key support level: 19,900; resistance: 20,200.  
- Focus sectors: IT, Pharma, and Banking.  
- Investors should watch out for inflation data and US Fed commentary.  
```

---

## 🧪 Running in Jupyter Notebook

You can use the `display_summary()` function for a clean, formatted output directly in your notebook.

```python
display_summary("https://example.com/some-news-article")
```

---

## 💡 Future Improvements

* Support **multiple URLs** at once.
* Add **language detection & translation**.
* Export summaries to **PDF / CSV / Notion**.
* Enable **caching** to avoid repeated requests.
* Integrate with **FastAPI / Streamlit** for a web UI.

---

## 🤝 Contributing

Pull requests and feature suggestions are welcome!
Please open an issue first to discuss what you’d like to change.


