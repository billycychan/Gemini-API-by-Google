## Function Calling

[Gemini_Function_Calling.ipynb - Colab (google.com)](https://colab.research.google.com/github/udacity/gemini-api-course/blob/main/demos/Gemini_Function_Calling.ipynb)

Gemini has the ability to call user-defined functions, and this feature is called function calling.

```python
def get_full_menu(service: str):
    """List all items on the menu of Gemini's Trattoria for the given service.

    Args:
        name: The type of service, lunch or dinner.
    """
    return ["Chicken Caesar Salad", "Margherita Pizza", "Spaghetti and Meatballs", "Eggplant Parmesan"]


def find_vegetarian_items(items: list[str]):
    """List all dishes in items that are vegetarian.

    Args:
        items: A list of dinner dishes.
    """
    return ["Margherita Pizza", "Eggplant Parmesan"]

def enter_restaurant():
    """You enter Gemini's Trattoria, moving the creaky door."""
    print("The door swings open, making a loud noise.")
    return True

functions = {"get_full_menu": get_full_menu,
             "find_vegetarian_items": find_vegetarian_items,
             "enter_restaurant": enter_restaurant}
```

```python
model = genai.GenerativeModel(
    model_name="gemini-1.5-flash", tools=functions.values()
)

chat = model.start_chat(enable_automatic_function_calling=True)

response = chat.send_message(
    "What items are on Gemini's Trattoria's dinner menu?"
)
print(response.text)
# The dinner menu has Chicken Caesar Salad, Margherita Pizza, Spaghetti and Meatballs, and Eggplant Parmesan. 
```



### Multiple Function Call

```python
chat = model.start_chat(enable_automatic_function_calling=True)

response = chat.send_message(
    "Your are standing outside of Gemini's Trattoria. Enter the restaurant and read out the items on the menu."
)
print(response.text)
"""
Here, we can see that we used two functions, enter_restaurant() and get_full_menu().
The door swings open, making a loud noise.
Welcome to Gemini's Trattoria! Tonight we have Chicken Caesar Salad, Margherita Pizza, Spaghetti and Meatballs, and Eggplant Parmesan. 
"""

```

