## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:

### DESIGN STEPS:

#### STEP 1:

Design a Multi-Parameter Prompt Template

#### STEP 2:

Select the Core Components (Model and Parser). Here, my model is ChatOpenAI() and parser is StrOutputParser()

#### STEP 3:

Construct the LCEL Chain using pipeline (|) where this would connect the components together which are (prompt| model | output parser)

### PROGRAM:

import os
import openai

from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv()) # read local .env file
openai.api_key = os.environ['OPENAI_API_KEY']


from langchain.prompts import ChatPromptTemplate
from langchain.chat_models import ChatOpenAI
from langchain.schema.output_parser import StrOutputParser


prompt = ChatPromptTemplate.from_template(
    "tell me a short joke about {topic}"
)
model = ChatOpenAI()
output_parser = StrOutputParser()


chain = prompt | model | output_parser


chain.invoke({"topic": "robots", "style": "a children's rhyme"})


chain.invoke({"topic": "artificial intelligence", "style": "a news article"})

### OUTPUT:

<img width="1920" height="1200" alt="2025-11-13" src="https://github.com/user-attachments/assets/264fab50-79d7-4d06-bb1d-91c61eff4308" />


### RESULT:

The LangChain Expression Language (LCEL) chain was successfully designed and implemented. The program effectively utilized a ChatPromptTemplate with two parameters (topic and style), a ChatOpenAI model, and a StrOutputParser.
