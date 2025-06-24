<h1 align=center> AutoResearcher: Multi-Agent Autonomous Research Assistant </h1>

-----

### Autonomous Research Assistant Agents
Multi-agent system that takes a high-level research topic (e.g., “AI in Healthcare”) and:

- Gathers papers (Researcher Agent)
- Summarizes findings (Summarizer Agent)
- Creates a presentation (Designer Agent)
- Prepares FAQs (QA Agent)

##### Tech Hooks:
- Arxiv API / Semantic Scholar API
- Embedding + vector DB for document storage
- LangGraph task coordination
- Streamlit dashboard to preview slides and summaries
-----


```
                     ┌────────────────────┐
                     │   User Interface   │
                     │   (Streamlit App)  │
                     └────────┬───────────┘
                              │
                  ┌───────────▼────────────┐
                  │      LangGraph         │
                  │ (Task & Agent Routing) │
                  └──────────┬─────────────┘
                             │
      ┌──────────────────────┼────────────────────────┐
      ▼                      ▼                        ▼
┌──────────────┐     ┌─────────────┐           ┌─────────────┐
│ Researcher   │     │ Summarizer  │           │  Designer    │
│   Agent      │     │   Agent     │           │   Agent      │
│ (arXiv API + │     │ (LLM-based  │           │ (Generates   │
│  scraping)   │     │  summarizer)│           │  slides/text)│
└──────┬───────┘     └──────┬──────┘           └──────┬───────┘
       │                   │                          │
       ▼                   ▼                          ▼
 ┌──────────────┐   ┌─────────────┐           ┌──────────────┐
 │ Vector Store │   │ Summaries DB│           │ Output Slides│
 │ (FAISS/Chroma)│  │             │           │ (Markdown/PDF)│
 └──────────────┘   └─────────────┘           └──────────────┘
                             │
                             ▼
                      ┌────────────┐
                      │  QA Agent  │
                      │ (Gen FAQs) │
                      └────────────┘
```



```bash
conda create -n autores-agent python=3.12 -y
```