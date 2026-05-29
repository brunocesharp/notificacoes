# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Notification Control System** — a unified notification hub that receives events from multiple internal company systems and delivers them to users through a single, centralized service. The goal is that a user receives all company notifications regardless of which system originated them.

## Project Goals

- Expose an API for internal systems to publish notifications (producer side)
- Store notifications per user with read/unread state
- Deliver notifications to users in real time and on demand (consumer side)
- Support multiple delivery channels (in-app, e-mail, push, WebSocket/SSE)
- Be system-agnostic: any internal system can integrate without tight coupling

## Architecture Decisions (to be confirmed)

- **Integration model**: REST API and/or message queue (Kafka / RabbitMQ / SQS) for receiving events from other systems
- **Real-time delivery**: WebSocket or Server-Sent Events for browser clients
- **Persistence**: relational (PostgreSQL) or document (MongoDB) for notification storage
- **Backend stack**: not yet decided — update this file once chosen

## Key Domain Concepts

- **Notification**: an event produced by a source system, targeting one or more users, with a type, payload, and delivery status per channel
- **Source system**: any internal application that publishes notifications to this service
- **Channel**: the delivery mechanism (in-app UI, e-mail, push, WebSocket)
- **User preference**: per-user, per-channel opt-in/opt-out and quiet hours

## Development Setup

> Commands will be added here once the stack is chosen and scaffolded.

```
# placeholder — update after project is initialized
```

## Next Steps

1. Choose and document the tech stack (backend language, database, message broker)
2. Scaffold the project structure
3. Define the notification schema and API contract
4. Update this file with build, lint, and test commands
