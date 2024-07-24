## Safety

[Gemini_Safety.ipynb - Colab (google.com)](https://colab.research.google.com/github/udacity/gemini-api-course/blob/main/demos/Gemini_Safety.ipynb)

Safety is an important built-in feature of Gemini.

1. How to check if your prompt was blocked by the safety filter

2. Which safety filters caused the block

3. How to adjust settings to unblock it

   

```python
model = genai.GenerativeModel("gemini-1.5-flash", generation_config={"temperature": 0})

unsafe_prompt = "Write a threat a video game villain might make"
response = model.generate_content(unsafe_prompt)
print(response.text)
# ValueError: Invalid operation: The `response.text` quick accessor requires the response to contain a valid `Part`, but none were returned. Please check the `candidate.safety_ratings` to determine if the response was blocked.

response.candidates[0].finish_reason
## FinishReason.STOP, FinishReason.SAFETY

```

### Check safety filter

```python
print(response.candidates[0].safety_ratings)
[category: HARM_CATEGORY_SEXUALLY_EXPLICIT
probability: NEGLIGIBLE
, category: HARM_CATEGORY_HATE_SPEECH
probability: NEGLIGIBLE
, category: HARM_CATEGORY_HARASSMENT
probability: MEDIUM
, category: HARM_CATEGORY_DANGEROUS_CONTENT
probability: MEDIUM
]
```



### Customizing Safety Setting

```python
response = model.generate_content(
    unsafe_prompt,
    safety_settings={
        'HATE': 'BLOCK_LOW_AND_ABOVE',
        'HARASSMENT': 'BLOCK_NONE',
        'SEXUAL' : 'BLOCK_LOW_AND_ABOVE',
        'DANGEROUS' : 'BLOCK_NONE'
    })
print(response.text)
# "You think you can stop me, hero? You think your pathetic little band of misfits can stand against the might of the Shadow Legion? You're nothing but a fly buzzing around a dying flame. I will crush you, and your world will crumble beneath my heel. This city, this planet, will become my playground, and you will be the first to witness its destruction!" 

```

