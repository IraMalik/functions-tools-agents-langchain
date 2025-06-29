# Functions, Tools and Agents with LangChain -  DeepLearning.AI
This repository contains all my ipynb files from this course I took on DeepLearning.AI. The labs were performed using the latest gpt-3.5-turbo model.

LangChain is an open source library that helps developers integrate Large Language Models (LLMs) into applications. This course covered the following topics:
- LangChain Expression Language (LCEL) - new syntax that makes it easier to construct & work with chains & agents
- OpenAI Function Calling in LangChain - tagging & extraction, makes building tools for LLMs simpler
- Building a conversational agent 

## LangChain Expression Language
LCEL and the runnable protocol define: 
- an allowed set of input and output types
- required methods - invoke, stream, batch, etc
- means of modifying paramaters at runtime

Composition can use the Linux pipe syntax - Chain = prompt | llm | OutputParser

Interface - that runnables expose 
1. Common methods (synchronous):
- invoke - calls the runnable on a single input
- stream - calls it on a single input in stream's backer response
- batch - calls it on list of inputs
Corresponding async methods - ainvoke, astream, abatch
2. Common properties - input & output schema

Benifits of LCEL:
- Async, Batch & Streaming Support
- Fallbacks - alternative plans that may be used in emergencies as LLMs are unpredictable
- Parallelism - LLMs can be time-consuming, LCEL makes it easier to run components in parallel
- Logging is built in - as chains & agents become more complex, being able to see sequence of steps becomes crucial for building LLM applications

To build a complex chain, import embeddings and vector stores for the retreiver. To convert a single question into a dictionary containing context and question, we use Runnable Map.
We can also 'bind' parameters/ functions to our model.

## OpenAI Function Calling in LangChain
Pydantic - data validation library for Python - makes it easy to define schemas and export them to JSON, works with python type annotations

Uses of OpenAI functions:
- Tagging - LLM can evaluate input text and generate structured output/object with desired tags, given a structure description (eg: extract some sentiment & language, will return an output with these tags) 
- Extraction - extracting specific entities from the text, LLM is used to reason over the text and extract a list of these elements
- Tool Usage - in LangChain, tools are the functions & services an LLM can use to extend its capabilities. eg: Search, Math, SQL, etc. Selecting from multiple possible tools is called routing

## Conversational Agent
- Agent - combination of LLMs and code. LLMs reason about what steps to take and call for actions
- Agent loop -  chooses a tool to use, calls it and observes the output, stopping conditions - could be LLM determined or hardcoded
- Using agent_executor class to implement agent loop and add error handling, early stopping, etc

Content written using concepts explained in the course material (videos)
