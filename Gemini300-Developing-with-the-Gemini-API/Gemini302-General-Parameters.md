## General Parameters

[Gemini_General.ipynb - Colab (google.com)](https://colab.research.google.com/github/udacity/gemini-api-course/blob/main/demos/Gemini_General.ipynb)

### Temperature

 the same prompt can result in wildly different outputs (non-deterministic)

```python
model_name = 'gemini-1.5-flash'
new_outputs = []
low_temp_model = genai.GenerativeModel(model_name, generation_config={"temperature": 0})
for i in range(5):
  response = low_temp_model.generate_content(prompt)
  new_outputs.append(response.text)
for index, sentence in enumerate(new_outputs, start=1):
    print(f"{index}. {sentence}")
```

```txt
1. Grab some friends, head to the Engineering Library for a late-night coding session fueled by pizza and caffeine, and brainstorm solutions to a challenging LeetCode problem. 
2. 
...
5...
```

### Max output length

```python
model_name = 'gemini-1.5-flash'
short_response_model = genai.GenerativeModel(model_name, generation_config={"max_output_tokens": 5})
prompt = "Help me choose a fun way to spend my Friday night as a CS major at Berkeley in a single one-sentence idea"
response = short_response_model.generate_content(prompt)
print(response.text)
```

```txt
Grab some friends and head
```

### Token counting

```python
token_n_model = genai.GenerativeModel(model_name, generation_config={"temperature": 0.0})
poem_prompt = "Write me a poem about Berkeley's campus"

prompt_token_count = token_n_model.count_tokens(poem_prompt)
output_token_count = token_n_model.count_tokens(response.text)
print(f'Tokens in prompt: {prompt_token_count} \n Estimated tokens in output {output_token_count}')
```

```txt
Tokens in prompt: total_tokens: 9
Estimated tokens in output total_tokens: 269
```

## 