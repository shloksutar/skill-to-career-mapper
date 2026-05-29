🤖 Agentic Skill-to-Career Mapper

This project demonstrates an AI agent built using LangChain and LangGraph that helps users research career trends and find real-time job openings. It acts as a Decision Support System, automating the research phase of career planning by fetching live data from disparate sources, synthesizing it, and providing actionable job opportunities based on real-time market conditions.


🚀 Project Overview

This project implements an Agentic AI System to bridge the gap between skill acquisition and job market opportunities.

🛠️ Key Technical Components:
Orchestration Layer (LangGraph & LangChain):

Utilizes create_agent to build a conversational agent capable of reasoning and executing tasks.
Memory Management: Implements InMemorySaver to provide the agent with 'short-term memory' (thread-based state), allowing for context-aware multi-turn conversations.
Model Integration:

Powered by Google Gemini 2.5 Flash (via langchain-google-genai). This model provides high-speed reasoning and complex instruction following.

Real-Time Tooling (Function Calling):

Market Intelligence: Integrated Tavily Search for deep-web research on industry trends, salary insights, and skill demand.

Live Job Retrieval: Developed a custom tool using the JSearch API (RapidAPI) to fetch real-time, entry-level job listings filtered by specific skill sets and locations.


Security & Best Practices:

Employs Google Colab's userdata secrets management to handle sensitive API keys (Gemini, Tavily, RapidAPI) securely.
📚 External Resources & API Credits
To replicate or extend this project, the following external services and APIs are utilized:

Google Gemini API: Provides the core LLM capabilities for reasoning and natural language generation.

Source: Google AI Studio
Tavily Search API: A search engine optimized for LLMs and AI agents, used here for real-time market research and trend analysis.

Source: Tavily AI
JSearch API (via RapidAPI): Used to retrieve real-time job listings from across the web. It provides structured data for job titles, descriptions, and application links.

Source: JSearch on RapidAPI

⚙️ Installation

To run this notebook, you'll need to install the necessary Python packages. You can do this by running the following commands in your notebook:

!pip install -q langchain
!pip install -qU langchain-google-genai
!pip install -q langchain-tavily


🔑 API Key Setup

This project requires API keys for Google Gemini, Tavily Search, and JSearch (via RapidAPI). Please follow these steps to set them up securely:

Obtain API Keys:

Google Gemini: Get your API key from Google AI Studio.

Tavily Search: Obtain your API key from Tavily AI.

JSearch (RapidAPI): Subscribe to the JSearch API on RapidAPI to get your x-rapidapi-key.

Store in Google Colab Secrets:

In Google Colab, go to the left panel, click on the "🔑 Secrets" icon.

Add your API keys with the following names:

GEMINI_API_KEY

TAVILY_API_KEY

RAPID_API_KEY


🚀 Usage :

Once the libraries are installed and API keys are configured, you can run the notebook cells sequentially. The agent is configured to respond to user queries about skill demand and job opportunities.

Example Query:

user_query = "Which jobs are most suitable for candidates who are familiar with Web Application Development?"

response = agent.invoke({
    "messages":[{"role":"user" , "content":user_query}]
},config=config)

pprint(response["messages"][-1].content)
The agent will then use the skill_demand_search_tool to research the skill and the search_jobs tool to find relevant job listings, presenting the results in a structured format.

