# Advanced RAG Agent

- I build reliable RAG agents using LangGraph, Groq-Llama-3 and Chroma using concept like
     - Adaptive RAG : build a Router for routing questions to different retrieval approaches
     - Corrective RAG : develop a fallback mechanism to progress with when the context retrieved is irrelevant to the question asked.
     - Self-RAG : develop a hallucination grader .i.e. fix answers that hallucinate or doesn’t address the question asked.
 
![image](https://github.com/AJlearner46/Advanced-Graph-Based-RAG-Agent/assets/99804336/12cc0704-89c0-47df-808d-be375393e70d)

 
## WorkFlow
- Based on the question the Router decides whether to direct the question to retrieve context from vectorstore or perform a web search.
- If the Router decides the question to be directed for retrieval from vectorstore, then matching documents are retrieved from the vectorstore otherwise perform a web search using tavily-api search
- The document grader then grades the documents as relevant or irrelevant.
- If the context retrieved is graded as relevant then check for hallucination using the hallucination grader. If the grader decides the response to be devoid of hallucination then present the response top the user.
- In case the context is graded as irrelevant then perform a web search to retrieve the content.
- Post retrieval , the document grader grades the content generated from web search .If found relevant the response is synthesized by using LLM and then presented.


## Technology Stack Used
- Embedding Model : BAAI/bge-base-en-v1.5
- LLM : Llam-3–8B
- Vectorstore : Chroma
- Graph /Agent : LangGraph
