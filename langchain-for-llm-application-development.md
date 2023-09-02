# Langchain for LLM Application Development
[Course Link](https://learn.deeplearning.ai/langchain/lesson/1/introduction)
- Open source development framework for LLM apps
  - Modular components
  - Common ways to combine components

## LangChain Models, Prompts and Output Parsers
- Why use prompt templates?
- Prompts can be long and detailed
- We can re-use good prompts
- There are prompts for common operations
- parser helps create structured outputs and prompts to generate them

## Memory
- LLM is stateless each transaction (input/output) is independent
- `ConversationBufferMemory`: complete history as is
- `ConversationBufferWindowMemory`: limited recent history
- `ConversationTokenBufferMemory`: limited number of tokens maps directly to cost of using LLMs
- `ConversationSummaryBufferMemory`: summary of the conversation so far

## Chains
- LLM Chain: combination of LLM and prompt
- Sequential Chains: combine multiple chains. Output of one chain is input to next
- Router Chain: redirect to specialized prompts based on output of one prompt

## Question Answer over Documents   
