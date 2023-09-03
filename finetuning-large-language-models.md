# Finetuning Large Language Models

## Why finetune?
- specializing general purpose model and with additional data and make it more specialized for a specific use case
- alternative to prompt engineering
- prompting is more suitable for generic use cases, side projects, prototypes
- finetuning is more suitable for domain specific, enterprise, production usage, privacy

## Where finetuning fits in?
- Pretraining - Giant corpus of data trained to do next word prediction (self supervised learning)
  - Learns language and knowledge
- Too expensive to train with giant corpus of data
- Finetuning
  - training further with more data
  - can be self supervised / curated label data
  - it is one of tool in toolbox
  - for generative tasks this is not well defined
  - we update the weights of entire model
  - same training objective of next word prediction
- What is happening in finetuning
  - can lead to behavior change
    - consistent responses, focussed, teasing capability without too much prompt engineering
  - gain knowledge or both of above
- Tasks to finetune
  - Text in text out
    - Reading - output less text, e.g. keyword extraction, routing, agents
    - Writing - output more text, e.g. chat, write email / code
  - Task clarity is key to success
- Steps for finetuning
  - Identify task
  - Check if LLM is good at that task
  - Get 1000 inputs and outputs for the task
  - Finetune small LLM on this data
- Concatenate input and output together to use as training data to finetune model
- Templates can be used to provide structure to these input output pairs

## Instruction finetuning
- teaches model to behave like a chatbot
- If the data is not very well structured for Q&A we can use prompt template, We can also another LLM to do this
- We can use ChatGPT(`Alpaca`) to do this
- Data Prep -> Training -> Evaluation -> Loop

## Data preparation
- High quality data is essential. Garbage data will result in bad responses
- Diversity is essential to cover various aspects of use case
- Using real data is more effective. Generated data has some patterns to it
- More data is helpful but not as important
- Data preparation steps
  - Collect instruction response pairs
  - Concatenate pairs
  - Tokenize, Pad, truncate
  - Split in train/test
- It is VERY IMPORTANT to use same tokenizer as the model
- Huggingface library helps figure out tokenizer for given LLM model
- Padding is necessary to handle variable length inputs that are part of same batch
- Truncation ensures max length of the input

## Training

## Evaluation and Iteration
- Evaluating generative models is very difficult
- Human evaluation with domain experts is most reliable
- Good test data is crucial
- Generalized
- Not seen in training data
- Elo comparisons is also popular
- Error analysis
  - Understand base model behavior before finetuning
  - Iterate on data to fix problems in data space
  - Misspellings, Too long, Repetitive text

## Practical Approach to finetuning
- figure out your task
- collect inputs and outputs
- generate data if you do not have enough data
- finetune small model
- vary amount of data given to the model
- evaluate LLM to know whether model is performing well
- collect more data to improve
- increase task complexity
- increase model size for performance
### tasks and model size
- expansion (writing) tasks are harder
- extraction (reading) tasks are easier
- combination of tasks is harder
- larger model is needed for harder tasks
- PEFT - parameter efficient fine tuning
- LoRA - reduces number of parameters to be trained
  - Train new weights in inference layer but freeze main weights during training
  - At inference merge with main weights  
