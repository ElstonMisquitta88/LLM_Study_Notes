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
