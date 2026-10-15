# What Langflow is, and where it fits

Langflow is a low-code builder for AI workflows and agents: you connect components on a visual canvas and serve what you build as an API or an MCP server. Its own documentation describes it as an open-source, Python-based, customizable framework for building AI applications, and its repository is written mostly in Python with about 155,700 stars (checked October 2026).

## A visual canvas for flows

Langflow's primary job is to create and serve flows, which its documentation calls the functional representation of an application workflow. You build one by connecting and configuring component nodes, each a single step, and you test it in an interactive playground before wiring it into anything else. The documentation lists chatbots, document analysis systems, content generators and agentic applications as things teams build this way ([Langflow documentation](https://docs.langflow.org/)).

## Python components you can edit

The canvas is the main way to build, and it is not the only one. Langflow's repository states that source code access lets you customize any component using Python, and that you can use custom components built by others or develop your own ([langflow-ai/langflow](https://github.com/langflow-ai/langflow)). A flow also exports as JSON, so the same definition can live inside a Python application.

## Serving a flow as an API or an MCP server

A finished flow is meant to be consumed. Langflow ships built-in API and MCP servers, so a flow becomes a tool an application or an MCP client can call, and it also deploys as a conventional API. The same repository lists multi-agent orchestration with conversation management and retrieval, observability through tools such as LangSmith and LangFuse, and support for all major LLMs, vector databases and AI tools ([langflow-ai/langflow](https://github.com/langflow-ai/langflow)).

## How a team runs it

Langflow runs as a Python package, as a Docker image, or as a desktop app for Windows and macOS. From a fresh directory, the repository's quickstart is `uv pip install langflow -U` followed by `uv run langflow run`, which serves the app at http://127.0.0.1:7860. A Docker image and a Compose file ship for self-hosting, and the repository states that official release images require authentication by default ([langflow-ai/langflow](https://github.com/langflow-ai/langflow)).

## Where the configuration lives

A flow lives inside a Langflow project. You edit it in the app, and it can be exported as JSON, but the canvas, the projects and the served flows are the product's own state. The team does not commit or review them in a repository. That is the line between a builder and a system a company owns.

## Where Kortix fits

Langflow answers what a flow should do. Kortix answers where the work runs and who owns the configuration. Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector in one git repo you own, with the agents working on real cloud computers. An agent is `agents/<name>.md` (behavior) plus an `agents.<name>` block in `kortix.yaml` (governance), so the whole system is something a person can read and audit ([Kortix docs](https://kortix.com/docs)).

Continue with [A workflow canvas or a system you own](02-langflow-vs-owning-the-system.md).
