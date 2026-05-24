# to initialize uv 
pip install uv
uv init

# to make a venv we run
uv init
uv venv

# to install the lib
uv add -r re.txt

# to add jupyter notebooks
uv add ipykernel

# to add all the requirements in the txt so that i can know what it used
uv pip freeze > req.txt

# to check the version of the langchain
import langchain
langchain.__version__

# we have to use google this format to use the ai studio api key
from langchain_google_genai import ChatGoogleGenerativeAI

model = ChatGoogleGenerativeAI(
    model="gemini-2.5-flash",
    google_api_key=os.getenv("GOOGLE_GENAI_API_KEY")
)

else

modelgoogle = init_chat_model(
    "gemini-2.5-flash",
    model_provider="google_genai"
)

## for groq\
import os
from dotenv import load_dotenv
from langchain_groq import ChatGroq

load_dotenv()

model = ChatGroq(
    model="llama-3.3-70b-versatile",
    api_key=os.getenv("GROQ_API_KEY")
)

response = model.invoke("What is the capital of France?")

print(response.content)


### streaming -  its showing the generation one by one tokeb by token as the llm generates 

for chunk in model.stream("Explain AI"):
    print(chunk.content, end="")


### Batching means sending multiple requests together in one operation to  save tokens

responses = model.batch([
    "What is AI?",
    "What is Docker?",
    "What is Kubernetes?"
])

for r in responses:
    print(r.content)
