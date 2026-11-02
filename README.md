## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:

To develop an LCEL-based application that accepts two input parameters, namely topic and audience, and generates a simple explanation with a practical example using a language model. The application combines a prompt template, a language model, and an output parser using the LCEL pipe operator.
### DESIGN STEPS:


#### STEP 1: Import Libraries and Configure the API Key

Import the required LangChain libraries, including ChatPromptTemplate, ChatOpenAI, and StrOutputParser. Configure the OpenAI API key securely to access the language model.

#### STEP 2: Create the Prompt Template and Initialize the Model

Create a prompt template using two parameters: topic and audience. Initialize the OpenAI language model and create a string output parser to convert the model's response into readable text.

#### STEP 3: Build and Execute the LCEL Chain

Combine the prompt template, language model, and output parser using the LCEL pipe operator (|). Pass the input values using the invoke() method, generate the response, and display the output. Test the chain with different real-world topics.

### PROGRAM:
```
%pip install -U langchain-core langchain-openai

import os
from getpass import getpass

from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
from langchain_openai import ChatOpenAI



if not os.getenv("OPENAI_API_KEY"):
    os.environ["OPENAI_API_KEY"] = getpass("Enter your OpenAI API key: ")



prompt = ChatPromptTemplate.from_template(
    "Explain {topic} in simple English for {audience}. "
    "Give a short explanation and one practical example."
)



model = ChatOpenAI(model="gpt-4.1-mini", temperature=0)



output_parser = StrOutputParser()



chain = prompt | model | output_parser



result = chain.invoke({
    "topic": "BTS",
    "audience": "ARMY"
})


# Step 7: Display the result
print("LCEL OUTPUT:")
print(result)


```

### OUTPUT:

<img width="1920" height="1080" alt="Screenshot (210)" src="https://github.com/user-attachments/assets/3e54ccae-52fa-4169-8e38-84dad8e2347e" />

<img width="1920" height="1080" alt="Screenshot (211)" src="https://github.com/user-attachments/assets/2c361cc6-e6b5-4ee9-9111-9afb0c0064ee" />



### RESULT:
