---
title: How to install Ollama and run models locally
slug: how-to-install-ollama-and-run-models-locally
tags:
  - Blog Posts
  - AI News
excerpt: Ollama is one of the simplest ways to run open models locally on macOS, Linux, or Windows without building a custom inference stack from scratch.
---

# How to install Ollama and run models locally

If you want to run open models on your own machine without building an inference stack from scratch, Ollama is one of the easiest starting points.

It gives you a local runtime, a simple CLI, and access to a large model library through a single workflow.

## Step 1: Install Ollama

### On macOS

Install the app from the official Ollama site, or use Homebrew if that is your preferred path.

### On Linux

Run:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

### On Windows

Download and install Ollama from the official website.

## Step 2: Start the Ollama service

On desktop installs, Ollama usually starts as part of the app or background service.

You can confirm the CLI is available by running:

```bash
ollama --help
```

## Step 3: Run your first model

A simple starting example is:

```bash
ollama run gemma3
```

The first time you run a model, Ollama downloads it. After that, it launches the model locally and opens an interactive prompt.

You can also choose an explicit size tag, for example:

```bash
ollama run gemma3:12b
ollama run llama3.1:8b
ollama run mistral
```

## Step 4: See what you have installed

To list downloaded models:

```bash
ollama list
```

To remove one you no longer need:

```bash
ollama rm gemma3:12b
```

## Step 5: Pick a model your machine can actually handle

This is where many people get stuck.

Do not start with the biggest model you can find. Start with something that fits your machine comfortably.

As a rough rule:

- smaller 1B to 8B models are easier for laptops and general testing
- mid-sized 12B to 27B models need more RAM or GPU headroom
- larger models can become slow or impractical without stronger hardware

If you care about speed and experimentation, smaller is often the better starting point.

## Step 6: Use the local API if you want app integration

Ollama also exposes a local API, usually on:

```text
http://localhost:11434
```

That means you can build local tools, scripts, chat interfaces, and RAG systems on top of it without sending requests to a cloud provider.

## Practical advice

If you are new to local models, start with one general-purpose model and learn its limits before downloading five more.

A good first pass is:

- `gemma3` for general local testing
- `llama3.1:8b` if you want a common baseline
- `mistral` if you want a compact general-purpose alternative

The point is not to collect models. The point is to pick one that fits your machine and your task.

## Sources

- [Ollama official site](https://ollama.com/)
- [Ollama GitHub repository](https://github.com/ollama/ollama)
- [Ollama model library](https://ollama.com/library)
