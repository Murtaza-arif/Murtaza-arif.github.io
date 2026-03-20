---
title: Amazon Bedrock AgentCore Stateful MCP Support Turns Agent Sessions into Production-Grade Workflow Units: The 2026 Rollout Playbook
tags: [AWS, Amazon Bedrock, AgentCore, MCP, Agent Engineering]
style: fill
color: primary
description: AWS added stateful MCP server features to Bedrock AgentCore Runtime, enabling elicitation, sampling, and progress updates in isolated sessions. Here is a practical rollout playbook.
---

# Amazon Bedrock AgentCore Stateful MCP Support Turns Agent Sessions into Production-Grade Workflow Units: The 2026 Rollout Playbook

The strongest AI engineering signal this week is not a new model. It is a runtime behavior shift.

On **March 10, 2026**, AWS announced that **Amazon Bedrock AgentCore Runtime now supports stateful MCP server features**. This adds stateful session support for capabilities like elicitation, sampling, and progress notifications, while preserving session isolation and MCP protocol alignment.

For teams building agent products, this is the difference between “single-shot tool calls” and genuinely interactive workflows that survive multi-step execution.

## Why this matters now

1. **Stateful interactions are now first-class in MCP on AgentCore**  
Features like elicitation and sampling can now be used in session-aware tool flows instead of forcing everything into stateless, one-turn patterns.

2. **Session context can be preserved across multi-step execution**  
In stateful mode, servers return an `Mcp-Session-Id` header and clients send it on subsequent requests, enabling continuity for long-running agent tasks.

3. **Complex workflows can become more user-trustworthy**  
Progress notifications let users see what the agent is doing during lengthy operations, reducing black-box behavior and abandonment.

## Practical rollout playbook

### 1. Split your agent tools into stateless and stateful lanes

Do not flip everything to stateful mode at once.

- keep deterministic lookups and short actions in stateless mode
- move multi-turn workflows (form completion, approvals, planning) into stateful mode
- document which tools require session continuity

This avoids unnecessary complexity while targeting the highest-value workflows first.

### 2. Standardize `Mcp-Session-Id` handling in every client path

Treat session ID management as infrastructure, not app logic.

- store and propagate `Mcp-Session-Id` for each active interaction
- implement re-initialize logic when sessions expire or return 404
- add correlation IDs so session and request traces can be joined in logs

Without this, stateful behavior will look flaky in production.

### 3. Design elicitation prompts as structured checkpoints

Elicitation should gather only decision-critical inputs.

- ask for missing values in bounded formats (dates, enums, limits)
- validate each response before advancing to the next step
- persist accepted values so retries do not restart the whole flow

This reduces failure loops and improves completion rates.

### 4. Use progress notifications for operations over 3-5 seconds

Progress updates should be explicit and stage-based.

- emit phases like `searching_data`, `calling_tools`, `drafting_output`, `awaiting_confirmation`
- surface progress in product UI, not just backend logs
- set timeout and cancellation behavior per stage

Agents that report progress are easier to debug and easier for users to trust.

### 5. Add release gates before production cutover

Require clear readiness criteria per stateful workflow.

- session continuity tests pass across reconnects
- induced expiry/restart cases recover correctly
- progress events appear in telemetry with no missing stage transitions
- median and p95 completion times stay within agreed SLOs

No release gate, no rollout.

## Concrete implementation example

A travel-ops assistant handling itinerary changes can move from stateless to stateful MCP in a two-week rollout:

- Days 1-3: classify existing tools into stateless vs stateful and define session ownership rules
- Days 4-6: implement session propagation and recovery behavior in API and UI clients
- Days 7-9: convert approval-heavy workflows to elicitation-based checkpoints
- Days 10-12: wire progress events to user timeline and operations dashboards
- Days 13-14: run canary traffic and failover tests under real workload patterns

Success criteria:

- 100% of stateful requests include valid `Mcp-Session-Id`
- no unrecovered session-expiry failures in canary window
- user-visible progress present for all long-running tool chains
- measurable drop in abandoned multi-step tasks

## Strategic takeaway

The important trend is not “MCP support exists.”

The trend is that **stateful agent runtime behavior is becoming a platform primitive**. Teams that treat sessions, elicitation, and progress as product architecture, not optional extras, will ship more reliable agent experiences at enterprise scale.

## Sources

- (2026-03-10, accessed 2026-03-20) AWS What’s New: [Amazon Bedrock AgentCore Runtime now supports stateful MCP server features](https://aws.amazon.com/about-aws/whats-new/2026/03/amazon-bedrock-agentcore-runtime-stateful-mcp/)
- (accessed 2026-03-20) AWS docs: [Stateful MCP server features - Amazon Bedrock AgentCore](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/mcp-stateful-features.html)
- (accessed 2026-03-20) AWS docs: [MCP protocol contract - Amazon Bedrock AgentCore](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/runtime-mcp-protocol-contract.html)
- (accessed 2026-03-20) Public LinkedIn discussion: [Amazon Bedrock AgentCore Runtime now supports stateful MCP server features](https://kr.linkedin.com/posts/woohyungchoi_amazon-bedrock-agentcore-runtime-now-supports-activity-7437358656674750465-MwlR)
- (accessed 2026-03-20) Public X discussion search: [Amazon Bedrock AgentCore Runtime stateful MCP on X](https://x.com/search?q=Amazon%20Bedrock%20AgentCore%20Runtime%20stateful%20MCP&src=typed_query&f=top)
