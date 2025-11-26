# Ragna

A Retrieval Augmented Generation app

Uses Streamlit, FastAPI, ChromaDB and the OpenRouter API

For a detailed explantion, read [ARCHITECTURE.md](./ARCHITECTURE.md)

## 📸 Screenshots
### Input UI

Upload a file + Ask a question
<img width="611" height="174" alt="image" src="https://github.com/user-attachments/assets/fb424d5e-ff86-4be5-987e-5ddc3ba24082" />
<img width="688" height="276" alt="image" src="https://github.com/user-attachments/assets/631dcf57-0aa4-425c-b3ae-aee83c46a53c" />
<img width="1359" height="675" alt="image" src="https://github.com/user-attachments/assets/1e750620-8083-477b-ae69-c14d6823ded7" />



### Output UI

Answer generated + Relevant retrieved context
<img width="859" height="587" alt="image" src="https://github.com/user-attachments/assets/1bf5edc0-3c43-43c5-b95a-fe2e5a159729" />
<img width="609" height="482" alt="image" src="https://github.com/user-attachments/assets/e6919eed-2e4c-4d6b-93fe-58c92f68b31b" />


## Steps to run

- First, you need to have the `uv` package manager installed, you can do that [here](https://docs.astral.sh/uv/)
- Clone the git repository using:
```bash
git clone https://github.com/sohan-sohan/ragna_new.git
```
- `cd` into `ragna_new`
- Create an OpenRouter API key [here](https://openrouter.ai/) and save the following into a `.env` file:
```bash
API_KEY = <your API key>
```
- Open a terminal and run the following commands:
```bash
uv sync # sets up the virtual environment with dependencies
uv run streamlit run frontend.py
```
- Open another terminal, `cd` into the `ragna_new` folder again, and run:
```bash
uv run uvicorn backend:app --reload
```
- The app will open in your browser
