# ChatGPT Prompt Engineering for Developers
[ChatGPT Prompt Engineering Course](https://learn.deeplearning.ai/chatgpt-prompt-eng)
## Types of LLMs
- **Base LLMs**
  - predict next word using text training data
- **Instruction tuned LLMs**
  - trained to follow instructions
  - A fine tuned version of Base LLMs
  - uses RLHF (reinforcement learning with human feedback)
  - for practical applications should be used rather than base LLMs

## Guidelines for prompting
- Principles
  1. Write clear and specific instructions
    - Longer text tends to be more specific  i.e. short text does not mean clear instruction
    - Use delimeters to clearly separate the input to be operated upon
      - Good delimeters `"""", ```, ---, < >, <tag> </tag>`
      - These delimeters also avoid prompt injections
    - Ask for structured output
    - Check whether input satisfies preconditions and output accordingly
    - Few shot prompting
  2. Give model time to think
    - specify steps required to complete task
    - instruct model to work out the solution instead of running to a conclusion
- Model limitations
  - Hallucinations: Could make statements that sound plausible but not true (Basically misinformation)
  - To reduce hallucinations: first ask to find relevant information and then ask questions based on the information

## Iterative prompt building
- Idea -> Prompt -> Experiment -> Error analysis -> Refine Idea -> Loop

## Summarizing

## Inference
- building predictions, NER etc

## Transforming
- translation, tone conversion, proofreading etc.

## Expanding
- opposite of summarization

## Chatbot
- build context to continue conversation
