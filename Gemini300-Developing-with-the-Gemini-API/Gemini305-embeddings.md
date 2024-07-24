## Embeddings



**Embedding Definition:**

Embeddings are **vectors** (represented as lists of decimal point numbers) that represent **words**, **documents**, **images**, and even **videos**. They're a list of numbers so that machine learning models can easily process them. They can be used in a wide variety of tasks like document search, anomaly detection, and text classification.

```python
data = 'Hi there, this is Gemini tutorial!'

embed_data = genai.embed_content(
    model='models/text-embedding-004',
    content=data
)

print(embed_data['embedding'][:10])
```



### Truncating Embeddings

```python
embed_data = genai.embed_content(
    model='models/text-embedding-004',
    content='Below is how you truncate data!',
    output_dimensionality=10 
)

print(len(embed_data['embedding']))
```



### Specifying Embeddings for Tasks

```python
data = 'Finally touching the grass!'

embed_data_1 = genai.embed_content(
    model='models/text-embedding-004',
    content=data
    # no `task_type` specification; defaults to `retrieval_query`
)

embed_data_2 = genai.embed_content(
    model='models/text-embedding-004',
    content=data,
    task_type='retrieval_document'
)

print(embed_data_1['embedding'][:10])
print(embed_data_2['embedding'][:10])
```

