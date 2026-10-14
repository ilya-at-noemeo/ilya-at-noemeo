### Ilya Ivensky — building [Noemeo](https://noemeo.com)

Noemeo is an AI critique partner for photographers: it scores, compares and
discusses photos in conversation, inside the editor (Lightroom Classic) they
already use. It's local-first: photos, sessions and agent checkpoints stay on
the user's machine, and the cloud is stateless compute that runs model calls
and manages accounts.

**Architecture across 10 repositories**

| Layer | Repository | What it holds |
|---|---|---|
| Agent | `noemeo-photo` | LangGraph agents (scoring, comparison, keywords, conversational workspace) behind a local FastAPI server and a Lightroom plugin; research studies on public benchmarks (AVA, ArtBench) |
| Agent kit | [`noemeo-agent-kit`](https://github.com/ilya-at-noemeo/noemeo-agent-kit) (public) | Product-agnostic driver toolkit: pluggable LLM transport, structured output, token usage, prompt hashing, logging |
| Photo infrastructure | `noemeo-photo-infra` | Terraform `photo-api`: Lambda chat proxy to models on AWS Bedrock, Cognito-gated activation keys, usage metering, guardrails |
| Shared platform | `noemeo-infra` | Identity (Cognito), networking, generic GPU inference |
| IAM | `noemeo-iam` | Least-privilege deploy roles, GitHub Actions OIDC trust, environment separation |
| Claude Code plugin | [`noemeo-roles`](https://github.com/ilya-at-noemeo/noemeo-roles) (public) | Skills, agents and hooks used across every repo: design review against a decision log, code review, research, IAM review |
| Foundations | `noemeo-foundation` | Principles and the Noemeo-wide decision log |
| Distribution | `marketplace-candidates` | Photo-critique Agent Skill packaged for Claude and Codex marketplaces |

Plus the public site [`noemeo-website`](https://github.com/ilya-at-noemeo/noemeo-website).

Most repositories are private. **Source available to employers on request:**
[ilya@noemeo.com](mailto:ilya@noemeo.com)
