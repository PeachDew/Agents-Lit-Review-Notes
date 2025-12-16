## Isnt context engineering just prompt engineering?
From: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents

Context Engineering is an **evolution** of prompt engineering, there are some key differences:

PromptE are methods for writing and organising prompts, specifically for one-shot outcomes.

ContextE is a set of strategies for curating and maintaining the optimal set of tokens during inference. This includes ALL information
 - Prompts
 - Tools: What information/actions agents have access to
    - efficient
    - self-contained
    - clear
 - Message History
 - External Data
 - Multi-step/complex reasoning 
    - eg chain-of-thought prompting
    - self reflection methods use external algorithms to assess predictions
    - Retrieval augmentation (RAG) pulls from specialised databases and knowledge graphs

This allows for **more capable** agents that operate over longer time horizons. PromptE focuses on the initial words wheras ContextE focuses on the whole state of information available to the LLM at any given time.

--- 
From Weaviate Book: https://8738733.fs1.hubspotusercontent-na1.net/hubfs/8738733/eBooks/Weaviate-Context-Engineering-ebook.pdf

PromptE is simply just "how you ask the questions".

Context Engineering is the discipline of designing the architecture that feeds an LLM the right information at the right time.
    - building bridges (retrieval/memory/tools) connecting the LLM to the outside world, making sure its responses are grounded in facts beyond training data

## Arent AI Agents just LLM with customised system prompts?
From: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents

Article's Agent definition: LLMs autonomously using tools in a loop.

While system prompts are importand, it is only one piece of the agent's context. Agents in a loop generate more and more data that must be managed and refined cyclically.

---
From Weaviate Book: https://8738733.fs1.hubspotusercontent-na1.net/hubfs/8738733/eBooks/Weaviate-Context-Engineering-ebook.pdf


## Why do you need 3 whole months? Whats the difficulty?
From: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents

### Context Rot
Because LLMs have limited context, as number of tokens increases, the model's ability to accurately recall information decreases. 

This challenge stems from its core transformer architecture, where each token has to attend to every other token, 
 = n^2 pairwise relationships for n tokens

## Solutions to context rot
To maintain coherence and goal-directed over tasks that exceed LLM's context window, there is a need for multi-step strategies

 - Compaction: Summarising conversation when it reaches near window limit, and reinitiating a new context with the compressed summary.
 - Structured Note-taking (Agentic Memory): Where an agent writes notes/memory OUTSIDE context window and pulls them back in later
 - Sub agents: Where a main agent delegates focused tasks to specialised sub-agents
    - eg subagents returning condensed distilled summary of their work
    - achieves separation of concern (dividing systems into distinct independent modules)

For a trendspotting module that researches, analyses and presents technology trends.

