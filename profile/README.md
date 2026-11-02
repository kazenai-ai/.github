# KazenAI

**A hard spending limit for every customer's AI.**

KazenAI checks each OpenAI or Anthropic call against that customer's limit before the call runs. Over the limit, the call doesn't happen, and a run receipt records why. It wraps the Python client you already use, so there is no proxy to route through.

```python
# python -m pip install "kazenai-finops[openai]"
from openai import OpenAI
from kazenai_finops import monitor

client = monitor(
    OpenAI(),
    agent_id="support-agent",
    business_subject_ref="cust:acme-42",
    max_budget_usd=5.00,
)
```

## Repositories

| Repo | What it is |
|---|---|
| [kazenai-core](https://github.com/kazenai-ai/kazenai-core) | The core SDK (`kazenai` on PyPI): limits checked before each call, the request gate, loop detection |
| [kazenai-finops-sdk](https://github.com/kazenai-ai/kazenai-finops-sdk) | `kazenai-finops` on PyPI: the SDK most people install, with per-customer attribution |
| [kazenai-demo-agent](https://github.com/kazenai-ai/kazenai-demo-agent) | Runnable offline demos of hard spending limits for OpenAI and Anthropic agents, with no provider keys |
| [kazen-event-schema](https://github.com/kazenai-ai/kazen-event-schema) | The shared event contract used by the SDKs and Agent FinOps |

## Supported today

Python 3.10+. OpenAI Chat Completions and Responses, Anthropic Messages, sync and async, streaming and non-streaming; LangChain, LangGraph, CrewAI and LiteLLM. Not supported: OpenAI Realtime, Bedrock/Vertex wrappers, AutoGen.

## Links

[Docs](https://docs.kazenai.com/getting-started/) · [kazenai.com](https://kazenai.com/) · [Security advisories](https://github.com/kazenai-ai/kazenai-core/security/advisories) · founder@kazenai.com
