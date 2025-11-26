
# Architecture
This is a detailed explanation of how the app works

#📸 Screenshots
Input UI

Upload a file + Ask a question

<img src="./docs/input_ui.png" width="800">
Output UI

Answer generated + Relevant retrieved context
(Add your actual screenshot here.)

<img src="./docs/output_ui.png" width="800">

When you run

```bash
streamlit run frontend.py
uvicorn backend:app --reload
```

the frontend and backend servers are started respectively

The Streamlit UI asks you to **Upload a file** and **Enter a Question**

When you have done both of these and click on the Submit button:
- The file is sent to the `/processfile` endpoint of the backend server via a `POST` request

- The question is sent to the `/question` endpoint of the backend server via a `POST` request

- The `/processfile` endpoint receives the file and loads the file as binary data

- The backend server then uses the [`chunk_and_populate()`](./chunking.py#L5) function, that creates a ChromaDB collection, splits the received file into chunks and embeds each chunk into the collection

- The collection returned is stored as a global variable in the backend server in order to enable other endpoints to access it

- The `/question` endpoint receives the question that the user entered

- The backend then uses the [`retrieve_top_n()`](./database.py#L4) function to retrieve the top-n chunks from the collection that are relevant to the user's question

- When the relevant chunks are retrieved, the question along with the chunks are constructed into a prompt

- This prompt is sent to an LLM using the [`get_rag_answer()`](./llm.py#L16) function through the OpenRouter API

- The API returns a response which is returned by our `/question` endpoint back to our Streamlit server along with the relevant chunks

- This answer and the relevant chunks are displayed in the Streamlit UI to the user
