# Project Olympus

A command-line tool that takes a product idea and gathers simulated stakeholder feedback on it. It uses CrewAI with OpenAI's GPT-4 to run a few agents, each playing a different Accounts Payable (AP) role, then compiles their feedback into a single markdown report.

I built it as a hackathon project to try out agent-based workflows with CrewAI.

## What it does

You enter a product idea. The tool runs several agents, each playing an AP stakeholder:

- AP Processor
- Director of Accounts Payable
- System Administrator

Each one reviews the idea and lists the features that would help in their role and their main concerns. A final compiler agent collects all of the feedback into one markdown document, grouped by feature and noting which roles asked for each.

The result is saved as a markdown file.

## Tools used

- Python
- CrewAI and crewai_tools
- LangChain with OpenAI GPT-4
- Serper API for web search
- python-dotenv

## Run it locally

You need an OpenAI API key and a Serper API key.

1. Clone the repo and install dependencies:
   ```
   git clone https://github.com/ajcondondev/project_olympus.git
   cd project_olympus
   poetry install --no-root
   # or
   pip install -r requirements.txt
   ```
2. Copy `.env.example` to `.env` and fill in `OPENAI_API_KEY` and `SERPER_API_KEY`.
3. Run it:
   ```
   python main.py
   ```
   It asks for a product idea, then runs the agents and writes the report.

## Project structure

```
main.py       entry point; sets up the agents and tasks and runs them
agents.py     the agent definitions (the AP stakeholder roles)
tasks.py      the tasks the agents run
file_io.py    saves the output to a markdown file
tools/        tools the agents can use
```

## Notes

There is no live demo. It runs from the command line and needs API keys, so it is not something I can host as a static page. Running it uses your OpenAI API quota.
