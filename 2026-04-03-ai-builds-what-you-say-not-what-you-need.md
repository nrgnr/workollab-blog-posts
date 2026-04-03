---
title: AI builds what you say, not what you need
slug: ai-builds-what-you-say-not-what-you-need
tags:
  - Blog Posts
excerpt: AI coding tools are powerful, but they are literal. That makes them fast at implementation and weak at judgment, product interpretation, and pushback.
---

# AI builds what you say, not what you need

One of the biggest misconceptions around AI coding tools is that they understand the product the way an experienced builder does.

They do not.

They are extremely good at turning instructions into output. But that is not the same thing as understanding intent, spotting missing requirements, or pushing back when the request itself is flawed.

## AI is literal

This is the core limitation.

If you ask for user roles, AI may add a `role` field and wire basic conditions around it. Technically, it responded correctly.

But a human with product and engineering experience immediately starts asking harder questions:

- What happens when permissions change mid-session?
- How do shared resources behave?
- What is the audit trail?
- How does this affect existing APIs?
- What is the migration path for current users?

That layer of interpretation is where a lot of real value lives. AI usually does not supply it unless someone else already thought it through first.

## Hidden features are still features

Real products depend on many things nobody explicitly asks for:

- sensible loading states
- useful error messages
- safe defaults
- confirmations before destructive actions
- graceful handling when a request fails
- accessibility that holds up in real use

A strong developer adds these almost automatically because they understand what users expect. AI will often skip them because the prompt never mentioned them.

That creates software that can look complete in a demo and still feel broken in practice.

## AI does not push back

This is another underrated issue.

Good builders say no all the time. They reduce scope. They reject brittle designs. They explain why a request will create maintenance pain later.

AI does not naturally do that. If you ask it to build the wrong thing, it will usually try to be helpful and produce the wrong thing quickly.

That is useful for output volume. It is dangerous as a substitute for judgment.

## The context window is not product understanding

Even when the model is strong, it is still working inside a bounded context.

It can see the files you gave it. It can reason about a local area of the system. But it does not hold the product in its head the way a human architect can. It does not naturally understand business tradeoffs, team history, unwritten constraints, or how one seemingly small decision can affect five systems later.

This is why AI-generated changes can look reasonable in isolation and still create problems at the system level.

## The right role for AI

None of this means AI coding tools are bad.

It means they should be used for what they are actually good at:

- accelerating implementation
- generating drafts
- reducing repetitive work
- exploring options quickly

They are strongest when someone else is still responsible for direction.

## What the best teams do differently

The teams getting real leverage from AI are not asking it to replace judgment. They are using it to amplify execution.

The human still has to:

- frame the problem correctly
- decide what matters
- reject bad paths
- see what is implied but unstated
- define what good actually looks like

That is why the gap between "AI can write code" and "AI can build the right product" is still so large.

AI builds what you say. Someone experienced still has to determine what you actually need.

## Sources

- [OpenAI: Prompt engineering best practices](https://platform.openai.com/docs/guides/prompt-engineering)
- [Anthropic: Long context prompting tips](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/long-context-tips)
- [Stack Overflow 2025 Developer Survey](https://survey.stackoverflow.co/2025)
