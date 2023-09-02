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
- Create an index over documents using vector store
- We can use `similarity_search` over this index to find matching documents
- `RetrievalQA` chain provides a convinience that creates a context over all docs and then asnwers query with that context
- There are multiple ways of creating context `map_reduce`, `refine`, `map_rerank`

## Evaluating LLM Applications
- Manual evaluation with example queries can be done but is not scalable
- We can use `QAGenerateChain` to generate Q-A pairs
- We can use `QAEvalChain` to evaluate generated outputs

## Agents
- LLM can be used as a reasoning engine given some context help you reason about things
- Different tools can be intgerated to answer queries specific context
