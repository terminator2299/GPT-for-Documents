# GPT Search

This repository shows how you can utilize GPT and ChatGPT (GPT 3.5 turbo) to answer queries from a text document.

Instead of making stuff up, you can make GPT answer queries from a text document. It does this by running a semantic similarity search between the text document and the query and then asking GPT to form a response based on the $top-k$ results.

Pretty sure this is not novel and someone out there might have made something similar to this, but my searches didn't return me any good result so here it is!

## Why?

I was using GPT the other day and I wanted it to crawl a text corpus to answer my questions from the given corpus' context.

Existing alternatives
- Passing in the document - It is not possible to pass in the entire document to the GPT as the token limit is `4097` tokens and so this won't be scalable with bigger documents (which kinda defeats the whole point).

- Fine-tuning - OpenAI allows one to fine-tune GPT for custom use-cases but you can't just fine-tune GPT again and again for any new text corpus. It's time consuming and bit of an overkill.

## How?

**TL;DR:** We pass in 'k' most similar sentences to the query over to GPT with a pre-defined prompt. GPT makes the decision to choose and form the right answer to the query. 

This application has two components - 
* Semantic Search Part - The user defined Query and the Text corpus are encoded by a Sentence transformer. These encodings are then used to obtain similarities between the query and each sentence in the text corpus. This is done with the help of cosine similarity and th![WhatsApp Image 2025-02-27 at 20 27 52](https://github.com/user-attachments/assets/0f789f64-7b17-4e6b-87ee-0e3c582e4200)
en selecting some "top-k" results (in order of similarity scores).
  
* GPT Inference - The sentences from the text corpus that correspond to those "top-k" scores (basically the most similar `k` sentences) and the original query are then given to the GPT with a pre-defined prompt. This will return the GPT's answer to the user query with the help of top results from the context (the text corpus in this case).

---

## 📌 Future Improvements

- PDF file upload and extraction
- Show top-K similar sentences before GPT response
- Add summarization mode
- Maintain query-response conversation history
- Optional authentication for private access
- Save answers as `.txt` or `.json`
- Track query stats and performance metrics
- Multilingual document & query support
- Toggle between GPT-3.5 and GPT-4 (if available)
- Add unit tests and CI support


That's all folks! If you like this, go ahead and give this repo a ⭐️


