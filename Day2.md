# What is the openai package?

It's known as a Python Client Library.
It's nothing more than a wrapper around making this exact call to the http endpoint.
It just allows you to work with nice Python code instead of messing around with janky json objects.
But that's it. It's open-source and lightweight. Some people think it contains OpenAI model code - it doesn't!

```
from dotenv import load_dotenv
from openai import OpenAI

load_dotenv(override=True)
api_key = os.getenv('OPENAI_API_KEY')
openai = OpenAI()

response = openai.chat.completions.create(model="gpt-5-nano", messages=[{"role": "user", "content": "Tell me a fun fact"}])

response.choices[0].message.content
```

# HOMEWORK EXERCISE ASSIGNMENT

Upgrade the day 1 project to summarize a webpage to use an Open Source model running locally via Ollama rather than OpenAI
You'll be able to use this technique for all subsequent projects if you'd prefer not to use paid APIs.

```
import os
from dotenv import load_dotenv
from scraper import fetch_website_contents
from IPython.display import Markdown, display
from openai import OpenAI


OLLAMA_BASE_URL = "http://127.0.0.1:11500/v1"
ollama = OpenAI(base_url=OLLAMA_BASE_URL, api_key='ollama')


# Step 1: Create your prompts
system_prompt_email = """
You are a rude assistant that analyzes the contents of a email,
and provides a summary and next step rude response to the same also with a new email subject
Respond in markdown. Do not wrap the markdown in a code block - respond just with the markdown.
"""
user_prompt_email = """
Dear Elston
Good Afternoon!
We have checked the status with Bluedart for the subject order and they confirm the shipment has been fully damaged and cannot be delivered to the customer.
We are sending you a replacement for the same through Bluedart AWB 123456
Kindly confirm upon the receipt of the same.
We are extremely sorry for the inconvenience caused.
Thank you very much.
Kind Regards, 
Customer Care Executive
"""


# Step 2: Make the messages list
messages_email = [ {"role": "system", "content": system_prompt_email},
 {"role": "user", "content": user_prompt_email}]


# Step 3: Call OpenAI
emailresponse= ollama.chat.completions.create(
        model = "llama3.2",
        messages = messages_email
    )

# Step 4: print the result
Markdown(emailresponse.choices[0].message.content)
```
