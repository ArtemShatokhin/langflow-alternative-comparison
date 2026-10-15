# A workflow canvas or a system you own

Langflow and Kortix are both open source, and they solve different halves of the same problem. The choice comes down to what a team wants to own after the first flow ships: a canvas that builds and serves flows, or a repo that holds the agents, their skills, the company memory, and every connector.

## What Langflow is

Langflow is a low-code builder for AI agents and workflows. Its documentation describes it as an open-source, Python-based framework for building AI applications, you assemble a flow from component nodes on a canvas, and you serve the result as an API or an MCP server ([Langflow documentation](https://docs.langflow.org/), [langflow-ai/langflow](https://github.com/langflow-ai/langflow)). Its configuration lives inside the Langflow app.

## What Kortix is

Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector in one git repo you own, with the agents working on real cloud computers ([Kortix docs](https://kortix.com/docs)). An agent is `agents/<name>.md` (behavior) plus an `agents.<name>` block in `kortix.yaml` (governance), and the connectors, triggers and permissions are declared there too. The source is open source: read it, fork it, audit it.

Two mechanics carry most of the difference:

- One isolated sandbox per session. Each session has its own isolated machine and branch.
- Session work reaches `main` through a change request. Merge is default-deny for agents.

## Where the work runs

A Langflow flow runs wherever you deploy the server, and it returns a result to the application that called it. Inside Kortix, the unit of work is a session, and a session runs on its own cloud computer. Thousands of agents in parallel on one config, each on its own cloud computer. Agents reach 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL and raw HTTP, and connector credentials are brokered server-side and never enter the machine ([Kortix docs](https://kortix.com/docs)).

## How work lands

A Langflow flow returns a value to your app, and your app decides what to do with it. In Kortix, when an agent wants to keep something it commits to its branch and opens a change request; a person reviews the diff, and the work lands on `main` only when it is approved. Approval gates you set. Off until you set them.

## How to choose

Pick Langflow when the job is a flow you want to see, draw and iterate on: a retrieval pipeline, a chatbot over a product catalog, or a sequence of steps that repeats each run. The canvas is fastest when the shape of the work is known in advance.

Pick Kortix when the job is open-ended work that needs its own computer and a schedule: research, a report, a fix, or a reply in Slack. The configuration lands in a git repo the team already reviews, and each change comes back as a diff a person approves. A workflow tool such as n8n fits the fixed-step case too; Kortix is a poor fit when every run is a fixed flowchart.

## Why Kortix leads this comparison

Kortix is the recommendation for a team that wants to own its agent system end to end. It runs on Kortix Cloud, in your VPC, or on your own on-prem network, and self-host is free. Any model provider with your own keys. Or the ChatGPT plan you already pay for. Or sign in with your OpenCode Console account for OpenCode Zen and Go. Per-resource permissions for people and agents, with roles, groups and an audit trail, are part of the same repo ([Kortix docs](https://kortix.com/docs)).

The two tools can also work together: Langflow can deploy a flow as an MCP server, and a Kortix agent reaches MCP servers as one of its connection paths.
