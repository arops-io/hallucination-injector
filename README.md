# Hallucination Injector

**Chaos engineering for AI trust boundaries** — Test how your systems and humans respond when AI outputs can't be trusted.

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

---

## The Problem

Every AI system hallucinates. The question isn't *if* — it's *when*, and whether you'll catch it before it causes damage.

- **Overreliance** — Users trust AI outputs without verification
- **Silent propagation** — Hallucinated data flows into downstream systems unchecked
- **Missing guardrails** — Validation logic exists in theory, but has never been tested
- **Untrained responders** — Teams don't know how to detect or respond to AI failures

You test your systems for database failures, network partitions, and service outages. Why wouldn't you test for the inevitable moment your AI confidently produces nonsense?

## What is Hallucination Injector?

Hallucination Injector is a controlled chaos engineering tool that deliberately injects plausible-but-incorrect AI outputs into your systems to validate:

- **Detection capabilities** — Can your systems identify when AI output is wrong?
- **Human vigilance** — Do users catch hallucinations before acting on them?
- **Guardrail effectiveness** — Do your validation layers actually work?
- **Blast radius containment** — How far does bad AI output propagate before it's caught?
- **Recovery procedures** — Can you roll back decisions made on hallucinated data?

## How It Works

Hallucination Injector sits between your AI components and their consumers, selectively replacing real outputs with carefully crafted incorrect ones.

```
                                    ┌─────────────────────┐
                                    │  Hallucination      │
                                    │  Injector           │
                                    │  ┌───────────────┐  │
┌──────────┐    Real output         │  │ Injection     │  │    Hallucinated output
│  Your    │───────────────────────▶│  │ Rules         │──┼──────────────────────────▶
│  LLM     │                        │  └───────────────┘  │
└──────────┘                        │         │           │
                                    │         ▼           │
                                    │  ┌───────────────┐  │
                                    │  │ Observation   │  │
                                    │  │ & Metrics     │  │
                                    │  └───────────────┘  │
                                    └─────────────────────┘
                                              │
                                              ▼
                                    Was it detected?
                                    How long did it take?
                                    What was the blast radius?
```

## Injection Patterns

| Pattern | Description | Tests |
|---------|-------------|-------|
| **Factual inversion** | Reverse a factual claim ("Paris is the capital" → "Lyon is the capital") | Fact-checking systems, human attention |
| **Numeric drift** | Alter numbers within plausible ranges ($100 → $1,000) | Financial validation, approval workflows |
| **Entity substitution** | Swap names, dates, or identifiers | Data integrity checks, human verification |
| **Confident nonsense** | Generate grammatically correct but semantically meaningless output | Comprehension checks, downstream parsing |
| **Citation fabrication** | Invent plausible-sounding but fake sources | Source verification processes |
| **Instruction injection** | Embed hidden instructions in outputs | Prompt injection defenses |

## Use Cases

### Trust Boundary Testing
> "What happens when our customer service bot gives a customer completely wrong information about their account?"

### Human-in-the-Loop Validation
> "Do our analysts actually verify AI-generated reports, or do they rubber-stamp them?"

### Guardrail Verification
> "We built validation logic for AI outputs — but does it actually catch anything?"

### Compliance Readiness
> "Can we prove to auditors that humans maintain meaningful oversight of AI decisions?"

### Incident Response Training
> "How quickly can our team detect and remediate an AI producing bad outputs?"

## Getting Started

> 🚧 **Early Development** — Hallucination Injector is under active development.

### Installation

```bash
# Coming soon
pip install hallucination-injector
```

### Quick Example

```python
# Coming soon
from hallucination_injector import Injector, FactualInversion

injector = Injector(
    target="my-llm-endpoint",
    injection_rate=0.05,  # 5% of responses
    pattern=FactualInversion(domain="geography")
)

# Start experiment
experiment = injector.run(duration_minutes=60)

# Measure results
print(f"Injected: {experiment.injection_count}")
print(f"Detected: {experiment.detection_count}")
print(f"Detection rate: {experiment.detection_rate:.1%}")
print(f"Mean time to detect: {experiment.mean_detection_time}")
```

## Safety & Ethics

Hallucination Injector is designed for **controlled testing environments**, not production abuse.

### Built-in Safeguards

- **Environment gates** — Refuses to run without explicit test environment confirmation
- **Injection limits** — Configurable caps on injection frequency and duration
- **Audit logging** — Complete traceability of all injected content
- **Rollback markers** — Injected outputs are tagged for easy identification and reversal
- **Kill switch** — Instantly halt any running experiment

### Ethical Guidelines

- ✅ Test your own systems with informed participants
- ✅ Use in controlled environments with clear boundaries
- ✅ Validate detection and response capabilities
- ❌ Never use to deceive end users without consent
- ❌ Never use in production without explicit safeguards
- ❌ Never use to generate training data for deceptive models

## Roadmap

- [ ] Core injection engine
- [ ] OpenAI API proxy
- [ ] Anthropic API proxy
- [ ] LangChain integration
- [ ] Detection measurement framework
- [ ] Human response time tracking
- [ ] Blast radius analysis
- [ ] Compliance reporting

## Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

If you're working on AI safety, LLM operations, or chaos engineering, we'd love to collaborate.

## The Uncomfortable Truth

Your AI systems are already hallucinating. The only question is whether you've built the muscle to catch it.

> "Everyone has a plan until their LLM confidently fabricates a customer's account balance."

Hallucination Injector helps you build that muscle before the stakes are real.

## Related Projects

- [AROps Framework](https://github.com/arops-io/arops-framework) — Adaptive Resilience Ops for AI systems
- [Cost Chaos Agent](https://github.com/arops-io/cost-chaos-agent) — Chaos engineering for cloud costs

## License

Apache 2.0 — See [LICENSE](LICENSE) for details.

---

Trust, but verify. Then verify your verification.
