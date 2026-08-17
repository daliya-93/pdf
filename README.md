# PDF Chatbot (LangChain + Claude)

A beginner project that loads a PDF, splits it into searchable chunks, and (in progress) lets you ask questions about its contents using Claude.

## Status

- [x] Load a PDF and read its contents
- [x] Split PDF text into chunks for searching
- [ ] Generate embeddings for each chunk
- [ ] Store chunks in a vector database (Chroma)
- [ ] Retrieve relevant chunks and answer questions with Claude
- [ ] Wrap it in a Streamlit UI

## Tech stack

- **LangChain** — orchestrates document loading, splitting, and retrieval
- **Claude (Anthropic API)** — the LLM that answers questions
- **fastembed** — generates embeddings locally (no extra API key needed)
- **Chroma** — local vector database for storing/searching chunks
- **Streamlit** — simple web UI (planned)

## Setup

1. **Clone/open the project folder** in VS Code.

2. **Create and activate a virtual environment**
   ```
   python -m venv venv
   venv\Scripts\activate
   ```
   (On Mac/Linux: `source venv/bin/activate`)

3. **Install dependencies**
   ```
   pip install langchain langchain-community langchain-anthropic pypdf chromadb streamlit fastembed python-dotenv
   ```

4. **Add your Anthropic API key**

   Create a `.env` file in the project root:
   ```
   ANTHROPIC_API_KEY=your_key_here
   ```
   Get a key at [console.anthropic.com](https://console.anthropic.com) → API Keys.

   ⚠️ Never commit `.env` to version control or share the key publicly.

5. **Add a PDF to test with**

   Place a PDF file in the project root and update the filename in `app.py` if needed (currently set to `pdf-test.pdf`).

## Running the project

```
python app.py
```

This currently:
1. Loads the PDF
2. Splits it into overlapping text chunks
3. Prints the number of pages, number of chunks, and a preview

## Project structure

```
pdf-chatbot/
├── app.py              # main script
├── pdf-test.pdf         # sample PDF for testing
├── .env                  # API key (not shared/committed)
└── venv/                 # virtual environment
```

## Notes / troubleshooting

- If you see `torch` DLL errors on Windows, this project avoids PyTorch entirely by using `fastembed` for embeddings instead of `sentence-transformers`.
- Make sure your terminal prompt shows `(venv)` before running any `pip` or `python` commands — otherwise packages may install to the wrong environment.
