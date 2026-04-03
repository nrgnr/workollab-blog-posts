---
title: How to move from AWS to Hetzner without making a mess
slug: how-to-move-from-aws-to-hetzner-without-making-a-mess
tags:
  - Blog Posts
  - Open Source
  - How-to Guides
excerpt: A cloud migration only works when you reduce complexity first. The safest path from AWS to Hetzner is usually simplification before lift-and-shift.
---

# How to move from AWS to Hetzner without making a mess

Many teams talk about leaving AWS when the bill gets painful, but a lot of migrations stall because the technical plan starts too late.

The mistake is treating migration as a hosting swap. In reality, the first job is to simplify what you are moving.

## Step 1: inventory what actually matters

Before touching infrastructure, identify:

- the workloads that are truly production-critical
- the managed services you depend on
- which systems are stateful
- which systems can tolerate downtime
- where your DNS, backups, and secrets live

This is where many migrations fail. People underestimate how much hidden AWS coupling sits inside a "small" stack.

## Step 2: reduce before you migrate

The safest migration is usually not a full lift-and-shift.

Instead:

- remove unused services
- collapse over-engineered networking
- simplify deployments
- replace cloud-specific dependencies where possible
- document what can become a plain VM, container, or managed database elsewhere

You want fewer moving parts before you move anything.

## Step 3: separate generic workloads from AWS-native ones

Some things move easily:

- Dockerized apps
- standard Nginx services
- worker processes
- Postgres or MySQL with clear backup plans

Some things do not:

- Lambda-heavy architectures
- tightly coupled IAM assumptions
- S3 event chains
- CloudFront-specific behavior

The migration plan gets much cleaner once you admit which pieces are portable and which pieces need redesign.

## Step 4: move stateless services first

Do not begin with the hardest database migration if you can first prove the deployment model with simpler workloads.

A good sequence is often:

1. stateless apps
2. background workers
3. non-critical internal services
4. databases and persistent storage

That lets you validate networking, monitoring, secrets, deployment scripts, and rollback procedures without placing the whole business at risk immediately.

## Step 5: keep rollback realistic

Every migration plan needs a real rollback path, not just confidence.

That means:

- backups tested before cutover
- DNS changes with sensible TTLs
- parallel validation where possible
- observability in the new environment before traffic moves

If rollback is vague, the migration is not ready.

## Step 6: accept that some redesign is healthy

A migration can be the best opportunity to remove waste:

- too many layers
- too many managed service dependencies
- too much cloud-specific glue
- too much spend defending complexity that does not help the business

The point is not to recreate AWS somewhere cheaper. The point is to end up with a system that is simpler, more understandable, and less expensive to operate.

## Sources

- [Hetzner Cloud documentation](https://docs.hetzner.com/cloud/)
- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- [Cloudflare DNS documentation](https://developers.cloudflare.com/dns/)
