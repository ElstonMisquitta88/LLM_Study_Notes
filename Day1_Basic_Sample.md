LLM Engineering: Master AI, Large Language Models & Agents

#### Installed Ollama and from Powershell ran the following commands


🧠 Command meaning: ollama serve

**ollama serve** is the command that starts the Ollama server process on your computer — it’s what allows other applications (like Cursor, VS Code, Jupyter, or APIs) to connect to your local large language models.

```
ollama serve
ollama run gemma3:270m
```
**Ctrl + D** to stop the conversation in Powershell

#### Git Clone of  https://github.com/ed-donner/llm_engineering/tree/main
#### Installed Cursor

Cursor Terminal
In Powershell - Installation of UV
```
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```
Then Run the following 
```
uv self update

uv sync
```

As we are not using Open AI paid versions, Using Ollama 3.2
The following command 


```
ollama pull llama3.2

ollama run llama3.2

```


In Cursor Install the followign extensions

Python

Jupyter

```
Basic Function Created
```

<img width="1036" height="538" alt="image" src="https://github.com/user-attachments/assets/8439201f-99aa-4d0c-9a8d-84818b6d1e9d" />

<img width="1027" height="227" alt="image" src="https://github.com/user-attachments/assets/b729d1fa-33fb-4b36-91f8-35877744a466" />


<img width="1068" height="463" alt="image" src="https://github.com/user-attachments/assets/83be4166-23d0-4b4d-93a3-380fabc6d754" />


```
 website = fetch_website_contents(url)
    response = openai.chat.completions.create(
        model = "gpt-4.1-mini",
        messages = messages_for(website)
    )
    return response.choices[0].message.content
```

```
Final Display
```


<img width="1048" height="690" alt="image" src="https://github.com/user-attachments/assets/70ad2c87-9269-46c2-81ed-19d32b54726c" />

#### Example Tried Out in Cursor

```
# Elston's Work

# imports

import os
from dotenv import load_dotenv
from scraper import fetch_website_contents
from IPython.display import Markdown, display
from openai import OpenAI

load_dotenv(override=True)
api_key = os.getenv('OPENAI_API_KEY')
openai = OpenAI()


# Step 1: Create your prompts
system_prompt_email = """
You are a smart assistant that analyzes the contents of a email,
and provides a summary and next step professional response to the same also with a new email subject
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
emailresponse=response = openai.chat.completions.create(
        model = "gpt-4.1-mini",
        messages = messages_email
    )

# Step 4: print the result

Markdown(emailresponse.choices[0].message.content)
```

#### Example Output

<img width="1516" height="431" alt="image" src="https://github.com/user-attachments/assets/94d7aaf9-9c19-438c-8e94-5234618494f1" />





