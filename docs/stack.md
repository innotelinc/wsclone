# AI Website Cloner in the Innotel Platform Stack

**Role: BuilderOps** — Clone any website into a clean Next.js app, with an AI coding agent.

Part of the [Innotel Platform Stack](https://github.com/innotelinc/innotel-platform-stack).
The canonical definition of the stack, its shared layers and their owners lives
there; this file records only what AI Website Cloner does inside it.

## Boundaries

### Owns

- the template app
- the cloning skills

### Consumes

- an AI coding agent
- the target site's public pages
- Cerulean Vault (deployment secrets, if hosted)

### Does not own

- the target site's content or rights
- the agent itself
- identity (Cerulean)

## Service map

| Component | Technology | Job |
| --- | --- | --- |
| AI Website Cloner | Node.js / TypeScript | Clone any website into a clean Next.js app, with an AI coding agent. |
| Identity | Cerulean Authentik | Sign-in and role claims, where the repo has a UI |
| Secrets | Cerulean Vault (KV v2) | Production credentials, referenced as `vault://` |
| Trust | Cerulean | DNS, TLS and the public hostname |
| Edge | NPM Edge | The public route in front of the service |

## In the ecosystem

- **Identity** comes from Cerulean Authentik; this repo holds no second account
  table and no password of its own.
- **Secrets** come from Cerulean Vault. `.env` is local only and is never
  committed; a `vault://` reference is resolved by the deployment.
- **Trust and edge** are Cerulean's and NPM Edge's. This repo does not write DNS
  records or call the NPM API directly.
- **Storage, billing and telephony** belong to ONYX, Magnate and Zeus
  respectively; AI Website Cloner consumes them only where the boundaries above say
  so.

## See also

- [README](../README.md)
- [Innotel Platform Stack](https://github.com/innotelinc/innotel-platform-stack)
