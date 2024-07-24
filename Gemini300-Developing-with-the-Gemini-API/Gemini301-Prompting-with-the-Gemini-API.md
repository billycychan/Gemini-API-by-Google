# Developing with the Gemini API

## Application Programming Interfaces (APIs)

An application programming interface (API) allows computer programs to communicate using a predetermined protocol. 

We interact with APIs using API keys. 

A key is a unique identifier that is passed along with API requests to authenticate the client making the request. It helps ensure that only authorized users or applications can access the API and its services.

Note that for the Gemini API, there are two ways of creating a key:

1. **Personal use**
2. **As part of an organization**. Note: You need to ask your admin owner to grant you access to the "Early Access Apps" setting!

## Prompting with the Gemini API

[Google Colab](https://colab.research.google.com/github/udacity/gemini-api-course/blob/main/demos/Prompts_With_Gemini_API.ipynb)

### Core Functionality of Gemini

#### Text
```python
prompt = """Create a free verse about the pasta Linguine. Make it descriptive
about the shape, taste, and texture of pasta. Make the poem at least five lines
long."""
response = model.generate_content(prompt)
print(response.text)

"""
Long, flat ribbons,
curving like a whispered secret,
each strand a whisper of flour and water,
slipping through the sauce,
a silken embrace of flavor. 
A dance on the tongue, 
a subtle chew,
yielding to the embrace of garlic,
the warmth of tomato,
the whisper of basil. 
A symphony of textures,
smooth and soft,
yet holding onto the richness,
a lingering echo of savory delight. 
Linguine, a simple song,
a melody of comfort,
a dance of flavor. 
"""
```
#### Image

```python
prompt="""This image contains a a kitchen with a seating area (four chairs),
cabinets, stove, a large window, and a knife holder. Give a description of the
following room, including the key components and each of the colors (be specific
about what exact shade) of the items. Explain in what location we could place 5
pots and pans so that the kitchen retains its minimalistic appeal and clutter
doesn't increase substantially."""
image_upload = genai.upload_file(path='kitchen.jpeg')
response = model.generate_content([prompt, image_upload])
print(response.text)
```

```txt
The kitchen features a minimalist design with a focus on clean lines and a neutral color palette. The focal point of the room is the large window that offers a view of the outside world. 

The cabinets are a soft white, with a slightly textured surface that adds a touch of depth.  The countertop is a cool white, and the backsplash is made of beige ceramic tiles arranged in a diamond pattern. The stovetop is black, and the sink is stainless steel.

The seating area consists of four wire-framed bar stools, in a silvery gray color, with a wooden base stained in a rich dark brown. The wooden base is made of planks,  resembling rustic reclaimed wood.

The floor is made of wood, stained in a rich brown hue with a warm undertone. There is a knife holder made of light wood, positioned on the countertop between the stovetop and the sink.

To retain the minimalistic appeal, the pots and pans can be stored in the following locations:

1. **Inside the cabinets:** This is the most practical and space-saving option.
2. **On a wall-mounted rack:** This will keep them organized and out of sight.
3. **Inside the oven:** If the oven is not in use, it can be used as a storage space.

The key is to choose a storage solution that is both practical and aesthetically pleasing. Avoid clutter and choose storage options that are visually appealing and blend with the minimalist design of the kitchen. 
```

#### Audio

```python
prompt = """Listen carefully to the following audio file, what's in it? What
mood does it set and what kind of film could it be used in?"""
audio_upload = genai.upload_file(path='summer-rainampthunder-162009.mp3')
response = model.generate_content([prompt, audio_upload])
print(response.text)
```

```txt
The audio file is a piece of ominous and suspenseful music, possibly a soundtrack for a film. It features a slow, building tempo with a haunting, drone-like sound that creates a sense of unease and anticipation. 

This music could be used in a variety of film genres, but it's particularly well suited for:

* **Horror:** The eerie and unsettling atmosphere is perfect for building tension and creating a sense of dread. 
* **Thriller:** The building tension and anticipation could effectively enhance a scene of suspense or mystery.
* **Science Fiction:** The drone-like sounds could be used to create a sense of vastness and otherworldliness.

The music is not overly specific to any particular plot or character, making it versatile for use in a variety of scenes and situations. 
```



#### Video

```python
prompt = """Describe the video. Describe how each tennis player hits the ball and
describe where the ball lands. Explain how the winning player positions the ball
to land in certain spots to win the point."""
audio_upload = genai.upload_file(path='summer-rainampthunder-162009.mp3')
response = model.generate_content([prompt, audio_upload])
print(response.text)
```

```txt
The video shows a tennis match from an aerial view. 

The first player is on the right side of the court and hits the ball with a backhand. The second player is on the left and returns the ball with a forehand. The ball lands just inside the line of the opposite player's court.  

The player on the right side moves to the left side of the court and hits the ball with a forehand. He hits the ball hard and straight to the left corner of the court, putting the ball out of reach of the opposing player. The opposing player is unable to return the ball because of its position on the court.  

The winning player was able to position the ball in the corner of the court by hitting it with a lot of power and aiming it straight. 
```

