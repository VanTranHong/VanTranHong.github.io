# Rethinking AI Agent Security: What Can We Learn from Computer Networks?

*AI agents are becoming increasingly autonomous. But how do we keep them secure when they can access sensitive data, communicate with external services, and make decisions on our behalf?*

Imagine asking an AI assistant to organize your next business trip. It checks your calendar, reads your emails, books flights, and coordinates meetings—all without requiring you to manage each step.

Now imagine that, while booking a hotel, it accidentally shares confidential meeting details with an external service. Or worse, a malicious webpage tricks it into sending sensitive information to an attacker.

These scenarios highlight a growing challenge: **the same capabilities that make AI agents useful also make them difficult to secure.**

In our paper, [*Rethinking Agent Security as a Networking Problem*](https://arxiv.org/abs/2608.12172), we explore a different way of addressing this challenge, drawing inspiration from decades of networking and systems security research.

Our central idea is simple: **Rather than trusting AI agents to secure themselves, we should build security mechanisms that independently control what they can do.**

## Why Can't We Simply Trust AI Agents to Behave Securely?

Many existing defenses focus on making AI agents behave more safely, through better instructions, guardrails, or training.

These approaches are valuable, but they have a fundamental limitation: they often depend on the agent itself to recognize and avoid unsafe actions.

What happens when an agent misunderstands an instruction? Or when a malicious document convinces it to ignore its security guidelines?

Even the most capable models can make mistakes or be manipulated.

**Security should not depend on an AI agent always making the right decision.**

This raises an important question: Can we design systems that remain secure even when the agent itself is unreliable?

## What Can Computer Networks Teach Us?

Computer networks have faced a similar challenge for decades: enabling communication between devices without assuming that every device can be trusted.

Rather than relying on devices to police themselves, networks use firewalls, access controls, and independent enforcement mechanisms to restrict unauthorized communication.

AI agents operate in increasingly similar environments. They access files, invoke APIs, communicate with services, and exchange information with other agents.

**What if we treated these interactions like network traffic—subject to independent security policies and enforcement?**

This changes how we approach agent security. Instead of asking whether an agent can recognize an unsafe action, we ask whether the surrounding system can prevent that action from happening.

## Bringing Networking Principles to AI Agent Security

Our work explores three principles for building more secure agent systems.

### 1. Separate Security from Agent Reasoning

In computer networks, the control plane defines communication policies, while the data plane enforces them.

We envision a similar separation for AI agents: a trusted security layer determines and enforces what actions are permitted, independently of the agent's reasoning.

An agent can decide what it wants to do, but **it should not have the authority to decide what it is allowed to do.**

### 2. Give Agents Only the Permissions They Need

AI agents often receive broad access to tools and sensitive resources, even when their tasks require much less.

Drawing on the principle of least privilege, we argue that agents should receive narrowly scoped permissions for specific resources and operations.

For example, an agent may be allowed to read a confidential report and share a summary with authorized colleagues—but not delete the report or send it to outsiders.

Limiting permissions reduces the damage an agent can cause if it makes a mistake or is compromised.

### 3. Consider the Context of Every Action

Not every technically permitted action is appropriate.

An agent might be authorized to read documents and send emails. But that doesn't mean it should share a confidential report with any recipient.

We therefore argue for combining **deterministic security policies** with **context-aware reasoning** that considers the sensitivity of information, the intended recipient, and the purpose of an action.

This allows security mechanisms to go beyond simply asking *“Is this operation allowed?”* and consider *“Is this operation appropriate in this context?”*

## What Would This Look Like in Practice?

To bring these ideas together, our paper proposes a network-inspired architecture that places an independent security component, called a **sidecar**, alongside each AI agent.

Think of the sidecar as a security checkpoint.

Whenever an agent attempts to access a resource, invoke a tool, or communicate with another service, the sidecar checks the action against policies defined by a trusted control plane.

Straightforward requests can be evaluated using deterministic rules, while more complex actions may require context-aware analysis.

The sidecar can then allow, block, or constrain the action without relying on the agent to enforce the decision itself.

**Even if an agent is manipulated, it should not be able to bypass the security boundaries established around it.**

This approach also offers a way to enforce consistent security policies across different agents, models, and applications.

## Toward a More Secure Agentic Future

As AI agents become more capable, we face a fundamental choice: should we continue relying primarily on making individual agents safer, or should we also rethink the systems in which they operate?

Our work argues for the latter.

There are still important challenges to address, from defining context-aware policies to enforcing them efficiently across dynamic multi-agent environments. Our proposed architecture is a starting point for exploring these questions.

But the broader lesson from networking is clear: secure systems are not built by assuming every component will always behave correctly. They are built with independent enforcement, limited privileges, and well-defined trust boundaries.

**The future of trustworthy AI is not just about building agents we can trust. It's about building systems that remain secure even when agents make mistakes.**

---

**Read our paper:** [*Rethinking Agent Security as a Networking Problem*](https://arxiv.org/abs/2608.12172)

*We welcome discussions and collaborations on AI agent security, network-inspired security architectures, and context-aware policy enforcement.*
