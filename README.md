# agent

Personal kuromaku seed: my own agent persona (Babis), rules, and flows. Used across projects via kuromaku's seed cascade.

## What's in here

```
agents/
  Babis.yaml          # personal agent persona -- Senior Design Engineer / AI Team Orchestrator
flows/
  design-review.yaml  # personal review flow
rules/                # rule library
  ai-engineering.md
  clean-code.md
  code-review.md
  compliance-first.md
  design-rigor.md
  gdp.md
  git-workflow.md
  issue-quality.md
  knowledge-ops.md
  naming-discipline.md
  quality-bar.md
  rust-developer.md
  yaml-schema.md
```

## Use it from another repo

In the consumer repo's `.kuro/config.yaml`:

```yaml
seeds:
  - path: .kuro/
  - path: ~/code/charemma/agent/
  - path: ~/code/nestrai/kuromaku/.kuro/
  - path: ~/code/nestrai/seeds/rust/

roles:
  writer:
    agent: Babis
    overlays:
      rules:
        - my-project-specific-rule
```

Kuromaku merges seeds in declaration order. Local `.kuro/` wins, then this seed, then upstream seeds. Overlays (kuromaku #364) let a project extend the seed agent with extra rules without copying the full file.

## See also

- [nestrai/kuromaku](https://github.com/nestrai/kuromaku) -- the runtime
- [nestrai/seeds](https://github.com/nestrai/seeds) -- shared seed cascades (rust, tex, generic)

## Conventions

- Agent persona files are ground-truth: edits here propagate to all consumer projects via seed cascade
- Rules are domain-scoped: if a rule belongs to "design-engineering generally", it lives here; project-specific rules stay in the project's own `.kuro/rules/`
- One topic per rule file -- no monolithic style guides
