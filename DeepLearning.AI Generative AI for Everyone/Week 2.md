
# Software applications.



## supervised learning

+ get labeled data. 1 month.
+ train model. 3 months.
+ deploy model. 3 months.

## prompt-based AI
+ Specify prompt, minutes/hours
+ Deploy (run) model, hours/days


```python
prompt = """
Classify the following review
as having either a positive or
negative sentiment: #(Instruction text)

The banana pudding was really
tasty! #(Review text)
"""
response = llm_response(prompt) # Code to call LLM
print(response) # Code to print output
```

[Trying generative AI- https://learn.deeplearning.ai/genai4e/lesson/1/activity1](https://learn.deeplearning.ai/genai4e/lesson/1/activity1)

```python
import openai
import os

openai.api_key = os.getenv("OPENAI_API_KEY")

def llm_response(prompt):
    response = openai.ChatCompletion.create(
        model='gpt-3.5-turbo',
        messages=[{'role':'user','content':prompt}],
        temperature=0
    )
    return response.choices[0].message['content']

prompt = '''
    Classify the following review 
    as having either a positive or
    negative sentiment:

    test.
'''

response = llm_response(prompt)
print(response)
```

```python
import openai
import os 

openai.api_key = os.getenv("OPENAI_API_KEY")

def llm_response(prompt):
    response = openai.ChatCompletion.create(
        model='gpt-3.5-turbo',
        messages=[{'role':'user','content':prompt}],
        temperature=0
    )
    return response.choices[0].message['content']
    
all_reviews = [
    'The mochi is excellent!',
    'Best soup dumplings I have ever eaten.',
    'Not worth the 3 month wait for a reservation.',
    'The colorful tablecloths made me smile!',
    'The pasta was cold.',
    'test',
    'good and not good'
]

all_reviews    

all_sentiments = []
for review in all_reviews:
    prompt = f'''
        Classify the following review 
        as having either a positive or
        negative sentiment. State your answer
        as a single word, either "positive" or
        "negative":

        {review}
        '''
    response = llm_response(prompt)
    all_sentiments.append(response)

all_sentiments

```

## Lifecycle of a generative ai project

+ scope project
+ build/improve system. initially a prototype (several days)
+ internal evaluation.
+ deploy and monitor.

### tools to improve performance.

+ Building Generative AI is a highly empirical (experimental) process – we repeatedly find and fix mistakes.
  + Prompting
  + Retrieval augmented generation (RAG). Give LLM access to external data sources.
  + Fine-tune models. Adapt LLM to your task
  + Pretrain models Train LLM from scratch


## cost intuition

+ token: word or subword.

## Retrieval Augmented Generation (RAG) (provide more information to LLM)

  + Given question, search relevant documents for answer
  + Incorporate retrieved text into an updated prompt
  + Generate answer from the new prompt with additional context



+ new form of web search.


## fine-tuning  

+ To carry out a task that isn’t easy to define in a prompt


























