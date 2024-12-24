# Web Page Summarizor

Static/dynamic web page AI summarizor

This repository contains a Python-based website summarizer that uses Selenium for web scraping and OpenAI's API for generating summaries. The project includes the following key functionalities:

## Features

1. **Website Crawler:**
   - Utilizes Selenium (with undetected_chromedriver) to scrape JavaScript-rendered content from websites.
   - Extracts the title and main text content of a webpage, excluding navigation-related elements.

2. **OpenAI Integration:**
   - Uses OpenAI's GPT models to analyze and summarize the extracted content.

3. **Markdown Output:**
   - Displays the generated summary in Markdown format.

4. **Environment Variable Support:**
   - Reads sensitive data like API keys and target website URLs from a `.env` file for security and ease of configuration.

---

## Requirements

To run this project, you need the following:

- Python 3.8+
- Google Chrome (installed at `C:/Program Files/Google/Chrome/Application/chrome.exe` by default)
- The following Python packages:
  - `requests`
  - `python-dotenv`
  - `beautifulsoup4`
  - `undetected-chromedriver`
  - `selenium`
  - `openai`
  - `IPython`

---

## Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/sybtra/web-page-summarizor.git
   cd web-page-summarizor
   ```

2. **Set Up a Virtual Environment (Optional but Recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Create a `.env` File:**
   Add the following variables to your `.env` file:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   SITE_URL=your_target_website_url_here
   ```

---

## Usage

1. **Run the Notebook:**
   Open `main.ipynb` in Jupyter Notebook or Jupyter Lab and execute the cells sequentially.

2. **Display Website Summary:**
   The final cell in the notebook will call the `display_summary` function, which uses the `summarize` function to generate a summary of the target website specified in the `.env` file.

3. **Summarize Another Website:**
   Update the `SITE_URL` variable in the `.env` file or pass a new URL directly to the `display_summary` function.

---

## Key Components

### 1. **WebsiteCrawler Class**
This class handles web scraping using Selenium. It:
- Initializes a Chrome driver in headless mode to scrape website content.
- Waits for the main content of the webpage to load.
- Extracts the HTML and parses it with BeautifulSoup.

### 2. **Messages and Prompts**
- A `system_prompt` is used to guide the AI's behavior.
- The `user_prompt_for` function creates a detailed user query to feed into OpenAI's chat API.
- `messages_for` compiles the system and user prompts into the required format.

### 3. **Summarization Functions**
- `summarize(url)`: Fetches the website content, processes it, and returns a summary.
- `display_summary(url)`: Displays the summary in Markdown format using IPython's `Markdown` display.

---

## Example Workflow

1. **Check for OpenAI API Key:**
   The script validates the API key before proceeding.

2. **Scrape Website Content:**
   The `WebsiteCrawler` class is initialized with a URL, and the content is extracted and parsed.

3. **Generate Summary:**
   OpenAI's GPT model processes the website's content to generate a concise summary.

4. **Display Summary:**
   The result is displayed in Markdown format for easy readability.

---

## Notes

- Ensure Google Chrome is installed and accessible via the path specified in the script.
- Handle exceptions carefully, especially for dynamic or protected websites that may block bots.

---

## Contributing

Feel free to submit pull requests or open issues for improvements or bug fixes.

---

## License

This project is licensed under the MIT License.
