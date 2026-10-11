# mirai
**Mirai Agentic Browser -  A custom browser integrating seamless, secure AI-driven task automation. Currently, all of my code is privatized. Please read about my project in my README.**

**How does it work?**

Setup: User links API key to their LLM Agent of choice, such as their Anthropic API key, OpenAI API key, (full integration of any LLM supported by LangChain)

1. Offline, local Python “helper” tool continalluy parses & condenses current html page (util. llamaindex) in the background
2. Condensed page sent to LangChain’s user-selected agent (e.g. Anthropic API key)
3. Connected agent compares page contents against its enumerated commands
4. If enumerated commands allow for agentic action, agent relays action back to offline helper
5. Offline helper relays execution to browser shell -> checked & validated against hardcoded chromium -> browser execution
6. Helper captures updated (post-execution) state -> parsed & condensed current html -> LangChain API compares page to enumerated commands -> decides & relays new action. (& repeat)

**Program Architecture & Cybersecurity Decisions**

1. Security architecture in four words: “Agent requests, browser executes”.

Biggest security vulnerability in agentic-integrated programs: prompt injection.
Mitigated by limiting agentic behavior to enumerated commands, and each agentic action is validated against hardcode (modified chromium browser) prior to execution. 
Other notes: User API key stored in local keychain, only accessed by offline Python “helper”, cannot be accessed via browser.

2. Local html pre-processing via Py & LlamaIndex 

Why?: Modern web pages are too noisy to be sent to API without prior condensing. Allows for over 10-fold improvement in agentic processing time, while minimizing token usage.

**Thank you for reading!**
