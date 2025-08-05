# AI Website Brochure Generator

A simple Python utility that:

1. **Scrapes** a company’s website (landing page and other relevant pages)  
2. **Selects** the most relevant links (About, Careers, Mission, etc.) via an LLM  
3. **Generates** a short brochure in Markdown using an LLM  

Built around a small pipeline:
- **Website** class (using `requests` + `BeautifulSoup`) to fetch page title, text, and links  
- **get_links()**: calls a local LLaMA model (via `ollama` + OpenAI-compatible API) to pick out relevant pages  
- **create_brochure()**: fetches content from those pages and prompts the LLM to produce a brochure in Markdown  

---

## Features

- **Lightweight scraper**  
- **Link filtering** via system+user prompts to your local LLM  
- **Markdown output** ready to drop into a README, blog, or documentation  

---

## Requirements

- Python  
- `requests`  
- `beautifulsoup4`  
- `ipython`  
- `openai` (for the API shim to Ollama)  
- `ollama` (running a local LLaMA model named `llama3.2`)  

Install with:

```bash
pip install -r requirements.txt
```

## Quickstart
1. Run an Ollama LLM on your machine:
```bash
ollama pull llama3.2
ollama run llama3.2
```

2. Clone this repo and install dependencies:
```bash
git clone https://github.com/MohammadMoeinKeyvani/ai-website-brochure-generator.git
cd ai-website-brochure-generator
pip install -r requirements.txt
```

3. Open website_brouchure_generator.ipynb in Jupyter or VS Code and run all cells.

4. Generate a brochure:
```python
create_brochure("Your Company Name", "https://your-company-website.com")
```

## Configuration
- **Model name:** change `MODEL = "llama3.2"` in the notebook if you have a different local model.
- **Prompt tuning:** customize `system_prompt` and the JSON schema in the notebook to tweak link-selection logic or brochure style.
