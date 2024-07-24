# Introduction-to-LLMs-and-Gemini

## What are LLMs and What is the Gemini API

### Large Language Models (LLMs)

An LLM is a type of machine learning model that is trained on massive amounts of text. LLMs perform well at tasks like language generation and translation.

LLMs take "Text" and "Machine Learning" as input, and output "Language Generation" and "Translation"

### LLM and APIs

LLMs are typically built on the **Transformer** architecture, which requires substantial computational resources.

 In order to avoid overloading a typical computer, it often **run on dedicated hardware** and can be **accessed via an API**.



### Gemini API by Google

Gemini is a family of LLMs deveoped by Google. These models are good at
- Long context windows
- Multimodal understanding
- Integration into Google products and servers

## LLM Architecture In High Level

The transformer based arhitecture is the foundation of large language models.
Key components
- the input embeddings
  - The tokens entered by users are reffered to as inputs
    - Tokens can be thought of as equivalent to individual words in text
    - In reality, it's how LLMs break up sequences of text into sub units, words/random chunks of characters

  - Input are converted numerical representation now an input embeddings

- positional encodding
  - encode the position of each word in the input sentence as a set of numbers.
  - It preserves the order of words and is essential for maintaining the meaning of sentence.

- Encoder
  - processes input texts and generates a series of hidden states.
  - capture the meaning and context of the text
  - allowing the model to comprehend and generate relevant responses.
  - works by applying multiple layers of attention in normalization mechanisms to refine the input embedding and extract meaningful patterns statistically

- Decoder
  - generates the output sequence based on the encoded input sequence.
  - decoder leans to predict the next word by analyzing the words that come before it.

- Output Embedding
  - Converted into a numerical format 
  - undergo positional encoding

- The linear layer
  - maps the decoder output embedding to a higher dimensional space that match input space

- Softmax function
  - generate a prob distribution for each output token
  - determining the most likely next word in the sequence


![Transformer architecture diagram, with the encoder on the left and decoder on the right](https://video.udacity-data.com/topher/2023/December/658ca9d7_erin-slides-sandbox-transformer/erin-slides-sandbox-transformer.jpeg)

## LLMs vs Traditional ML Models

Two main differences architecture and data



### Architecture

LLMs are typically trained using the Transformer architecture, utlizing a computationally complex technique called the attention mechanism

Traiditonal ML models, might use neural networks. but they also might use simpler, less computationally complex algotirhms (e.g. linear regression/decision tree)

### Data

LLMs are trained on unstructured text data that does not require manual annotation.

In contrast, traditional ML models are typically trained on much smaller, labeled datasets. 



### Capabilities

Traditional ML models are trained to perform specific tasks.

LLMs are sometimes referred to as *foundation models* because they are so adaptable to different situations.  (can be fine-tuned with a similar to the datasets used to train traditional ML models)



### Comparison Table

| Attribute                | Traditional ML Models                                | LLMs                                        |
| ------------------------ | ---------------------------------------------------- | ------------------------------------------- |
| Architecture             | Varies; can be neural networks or simpler algorithms | Typically based on Transformer architecture |
| Training Data            | Structured                                           | Unstructured                                |
| Capabilities             | Targeted                                             | Broad                                       |
| Computational Complexity | Lower                                                | Higher                                      |



### LLM Tasks

- Text Generation (essay writing,  blogpost, code snippets generating. )
- Summarization (condenses its information into fewer words(article, report, paper))
- Translation (code/ languages)
- Information Retrieval (taking in a query, finding the most relevant information out of stored files or documents)

### Gemini Models

#### Gemini 1.5 Pro

- Enhanced version of the original Gemini 1.0 Pro
- Multimodal model
  - can process various types of data, including text, images, audio and video
- Long context window (can take in longer prompts than any other large-scale foundation model)

#### Gemini 1.5 Flash

- Lightweight version of Gemini 1.5 Pro
- Multimodal functionality 
- a context window of 1 million tokens
-  has lower latency and costs less to use

#### Text Embeddings

- It takes in text and produces text embeddings
  - A way to represent text data as a fixed-length vector of numbers
  - More efficient information retrieval
