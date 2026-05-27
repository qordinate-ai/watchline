# Watchline

Most agents today are still reactive. They respond when a user asks or wake up on a schedule and scan too much context.

That works for demos, but it falls short when agents need to monitor multiple tools, users, and changing workflows.

Watchline gives agents a simpler solution:

> "Tell me when this specific thing happens, then wake the right agent with the right event."

Examples include:

- A customer replies to a thread that requires follow-up.
- A meeting changes, prompting a related task to update.
- A GitHub issue matches a saved condition.
- A claim, ticket, invoice, or approval changes status.
- A high-priority event appears across email, calendar, Slack, CRM, support tools, or internal systems.

Instead of having each agent create its own polling loop, deduplication logic, trigger filters, and wakeup protocols, Watchline offers a shared event and filter layer.

## Why This Matters

Agents are evolving into workflow owners, not just chat interfaces.

This shift means they need to know the right time to act.

Basic approaches can get messy:

- Poll everything repeatedly.
- Push every webhook into the agent and let it sort through the noise.
- Hard-code one-off cron jobs.
- Build fragile per-integration trigger logic in every product.
- Wake costly downstream agents for irrelevant events.

Watchline is built around a more focused idea:

> Agents should only wake when a user-defined future event actually occurs.

This design makes agent systems more affordable, quieter, easier to audit, and more trustworthy.

## OpenClaw Plugin

NPM: https://www.npmjs.com/package/@watchline/openclaw-plugin  
GitHub: https://github.com/qordinate-ai/watchline-openclaw-plugin

The OpenClaw plugin allows OpenClaw agents to create and manage watches.

The plugin polls a Watchline channel and injects matched events back into OpenClaw sessions.

### Hermes Plugin

PyPI: https://pypi.org/project/watchline-hermes-plugin/  
GitHub: https://github.com/qordinate-ai/watchline-hermes-plugin

The Hermes plugin lets Hermes agents use Watchline as an event/wakeup layer.

It gives Hermes agents a way to register watches, keep track of active watches, and receive matching future events without building their own polling loop for every source.

This is useful for agents that need to keep working after the initial user request, especially when the next useful action depends on something changing in an external tool or workflow.

## WatchBench

GitHub: https://github.com/qordinate-ai/watchbench  
Dataset: https://huggingface.co/datasets/watchline/watchbench-email-v0

WatchBench is a benchmark for event routing in agent systems.

The first dataset, `watchbench-email-v0`, tests whether an agent/event layer can correctly decide which email events should trigger user-defined watches.

Current dataset details:

- 500 synthetic email events
- 20 resolved watch intents
- 10,000 binary watch-event labels
- 412 positive pairs

The initial report compares Watchline-style event routing with polling-style downstream agent evaluation.

## Contact

Website: https://watch.qordinate.ai/
Email: founders@qordinate.ai

If you are building an agentic product where users connect tools and expect the agent to act when things change, we would like to talk.
