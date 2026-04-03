---
title: Secret storage is not the same as secret delivery
slug: secret-storage-is-not-the-same-as-secret-delivery
tags:
  - Blog Posts
  - Operations
  - Open Source
excerpt: Teams get into trouble when they treat the place that stores secrets as the same thing as the system that injects them at runtime.
---

# Secret storage is not the same as secret delivery

One of the easiest ways to create security debt is to treat secret storage and secret delivery like they are the same problem.

They are related, but they are not identical.

A secret vault answers one question: where does the truth live?

A runtime injection system answers a different question: how does software receive the values it needs without people copying them around manually?

When teams collapse those two concerns into one vague workflow, they usually end up with secrets scattered across chat messages, shell histories, copied `.env` files, CI settings, and random deployment scripts.

## Storage is about source of truth

The storage layer should be where credentials are managed, rotated, and audited.

That means it should be the place people trust when they need to answer questions like:

- what is the current API token?
- who changed it?
- when should it be rotated?
- what service does it belong to?

That is a governance problem more than a runtime problem.

If that source of truth is weak, every environment becomes harder to reason about because nobody knows which copy is the real one.

## Delivery is about controlled exposure

Applications still need credentials at runtime. They need database passwords, API keys, signing secrets, SMTP credentials, webhook tokens, and other configuration values.

But that does not mean the app host should also become the place where humans maintain the canonical secret record.

The runtime side should focus on:

- injecting the right value into the right environment
- limiting which services can read which secrets
- reducing plaintext copying
- supporting rotation without chaotic manual edits

That is a very different responsibility from long-term storage.

## Why teams blur the two

The usual reason is convenience.

Someone says:

- the secret is already in the vault, so just use that directly everywhere
- or the secret is already in the runtime injector, so that becomes the source of truth

Both shortcuts create problems.

If the runtime layer becomes the primary record, you lose clarity around governance and rotation. If the vault becomes the only practical delivery path, people start pulling values by hand and pasting them into systems that should have received them automatically.

In both cases, the team thinks it simplified the workflow. In reality, it hid the boundary.

## Good secret flow is directional

Healthy systems usually have a one-way mental model:

- secrets originate in a source-of-truth system
- secrets are synchronized or injected into runtime systems
- applications receive only what they need
- humans avoid passing secrets around manually unless there is an exceptional reason

That directional model matters because it tells everyone where to update a value and where not to improvise.

Without that, every outage or rotation turns into a scavenger hunt.

## The real enemy is informal copying

Most secret problems do not begin with advanced attackers. They begin with ordinary operational habits:

- exporting secrets into shell sessions and forgetting they are there
- saving temporary `.env` files
- hardcoding credentials “just until deploy works”
- pasting tokens into deployment notes
- letting CI and runtime drift away from the vault record

The more manual copying a workflow requires, the less trustworthy it becomes over time.

That is why secret handling should be designed as a flow, not a pile of tools.

## Small teams still need separation

A small company may not need a huge security platform. It still needs conceptual clarity.

At minimum, the team should be able to answer:

- where is the official value stored?
- how does it reach runtime?
- who is allowed to retrieve it manually?
- what gets rotated first if something leaks?

If those answers are muddy, the stack is already more fragile than it looks.

## Secret discipline is operational discipline

People often discuss secret management as if it were a security-only topic. It is really an operations topic too.

Clear secret flow reduces:

- deployment drift
- onboarding confusion
- broken rotations
- emergency guesswork
- hardcoded credential sprawl

That is why the distinction matters so much. Storage is not delivery. Governance is not injection. A team that treats them as separate systems usually runs cleaner infrastructure.

## Sources

- [Vaultwarden project](https://github.com/dani-garcia/vaultwarden)
- [Infisical documentation](https://infisical.com/docs/documentation/getting-started/introduction)
- [OWASP Secrets Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html)
