# What Langflow costs, and where open-source Kortix fits

Langflow itself is free to run. The bill a team actually pays is hosting, model calls and the time to build and maintain the flows and the application around them. The same three lines decide what a Kortix deployment costs, with one difference: Kortix self-host is free, and its managed cloud is priced per seat.

## Is Langflow free?

Yes. Langflow's documentation describes it as an open-source, Python-based, customizable framework for building AI applications ([Langflow documentation](https://docs.langflow.org/)), and its repository states that Langflow is completely open source and can be deployed to all major clouds ([langflow-ai/langflow](https://github.com/langflow-ai/langflow)). You can read it, run it, fork it and audit it. Its own terms are permissive.

## What a Langflow team actually pays for

Three costs sit outside the software, and Langflow does not set any of them:

- Hosting. A Langflow server runs on a machine you own or rent. A small instance is cheap, and the cost grows with the traffic the served flows take.
- Model calls. Langflow supports all major LLMs and vector databases, and it does not supply them. You connect a provider and pay that provider for tokens and embeddings.
- Time. A flow is one artifact inside an application. The team still builds, reviews and maintains the app that calls the flow, and it revisits the flows as models and data change.

Langflow also offers a hosted Langflow Cloud. Its own site invites a team to sign up for a free cloud account and to deploy on an enterprise-grade cloud platform ([langflow.org](https://www.langflow.org/)).

## Where open-source Kortix fits

Kortix is open source, so the software is free to read, fork and audit, and self-host is free. On the managed side, Kortix Cloud Free includes 200 credits each month for sandbox compute and 1 project, and the team plan is $40/seat/month for 2,500 pooled credits per seat, optional managed model access, and seats for the people on your team ([Kortix pricing](https://kortix.com/pricing), checked October 2026).

Agent Computer compute is billed per second, per resource: $0.0000168/vCPU, $0.0000054/GiB RAM and $0.000000036/GiB storage, about $0.20 per hour for the default 2 vCPU / 4 GiB / 20 GiB machine, and $0 while stopped. Model calls work the same way as with Langflow: any model provider with your own keys. Or the ChatGPT plan you already pay for. Or sign in with your OpenCode Console account for OpenCode Zen and Go. If you choose Kortix-managed models, their tokens use Team credits. Kortix runs on Kortix Cloud, in your VPC, or on your own on-prem network ([Kortix pricing](https://kortix.com/pricing)).

## FAQ

### Is Langflow free to use in production?

The software is. A production deployment still carries the hosting, model and maintenance costs, because Langflow does not supply infrastructure or models.

### Does Kortix bill the people on my team?

On managed Kortix Cloud, the team plan includes seats for the people on your team. With self-host, the seats are not billed at all.

### Do I have to use Kortix's models?

No. Any model provider with your own keys. Or the ChatGPT plan you already pay for. Or sign in with your OpenCode Console account for OpenCode Zen and Go.

## Start with Kortix

Kortix is open source: your agents, their skills, your company memory, and every connector in one git repo you own. Start free on Kortix Cloud, or self-host for free ([Kortix](https://kortix.com)).
