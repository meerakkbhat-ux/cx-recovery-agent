# cx-recovery-agent
A hybrid Agentic AI prototype for Digital Customer Experience with AI classification, safety guardrails, human escalation, and next-best-action logic.

# CX Recovery Agent

A lightweight hybrid Agentic AI prototype for Digital Customer Experience.

The project analyses customer messages, classifies the issue using AI, applies deterministic safety and confidence guardrails, selects the next action, and decides whether human intervention is required.

## What it does

The agent can:

- classify customer issues such as safety problems, installation issues, technical malfunctions, documentation requests, usability issues, and service complaints
- assess urgency
- choose an action such as self-service, support-ticket creation, or human escalation
- recommend a next-best action
- generate a customer-facing response
- create an internal support note

## Architecture

Customer Message  
→ AI Intent Classification  
→ Safety Guardrails  
→ Confidence Check  
→ Urgency Assessment  
→ Action Selection  
→ Human-in-the-Loop Escalation  
→ Next-Best Action  
→ Customer Response + Internal Note

## AI approach

The prototype uses a zero-shot classification model from Hugging Face:

`facebook/bart-large-mnli`

AI is used for intent understanding, while deterministic rules are used for critical governance decisions.

For example:

- safety-related terms such as smoke, fire, sparks, or overheating always trigger a safety escalation
- low-confidence classifications are routed to a human instead of being handled autonomously

This hybrid design avoids relying entirely on probabilistic AI decisions for higher-risk customer situations.

## Example

Customer message:

`The charger started smoking.`

Output:

- Issue: Safety issue
- Urgency: Critical
- Action: Escalate to human
- Human required: Yes
- Next-best action: Arrange urgent technical inspection and prevent further charger use

## Why I built it

I built this project to explore how Agentic AI can support digital customer experience by combining AI-based understanding with workflow decisions, governance, and human escalation.

The goal was not to build a chatbot, but to create a simple system that can interpret a customer situation and decide what should happen next.

## Technologies

- Python
- Hugging Face Transformers
- BART Large MNLI
- Google Colab

## Future improvements

- connect the agent to a real knowledge base
- add automated ticket creation
- add customer history and context
- track resolution rates and escalation rates
- create a simple web interface
- add persistent customer-journey state
