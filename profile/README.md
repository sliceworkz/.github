# Sliceworkz

Open source libraries supporting modern Java software development,
based on Event Sourcing, EventModeling, Dynamic Consistency Boundary and Vertical Slice Architectures.


## Eventstore library

A DCB-compliant Eventstore implementation in Java, that supports your eventsourced applications.

Features:
- Java 21+
- Minimal dependencies (JDBC Driver, Connection pool, Json library and logging API)
- Postgres DB storage option with event append notifications to minimize eventual consistency delays
- In-Memory storage option for fast demo's and unit-testing
- Fully compliant with DCB (Dynamic Consistency Boundary) specification (https://dcb.events/specification/)
- Optimistic locking on Event appends
- Projection and Projector support classes that assist in implementing your event projections
- Non-opinionated approach: supports both Aggregate-less DCB-style approaches as wel as classical Aggregate-based implementations


## EventModeling framework

An opinionated EventModeling implementation framework, supporting applications in a Vertical Slice Architecture.
Builds on top of the Eventstore library.

Features:
- EventSourced BoundedContext implementations 
- Building blocks:
	- Events (Inbound-, Domain- and Outbound Events)
	- Commands: validates invariants and produces Domain Events
	- ReadModels: projects DomainEvents to a consumable, use-case specific view
	- Automations: combines a ReadModel as a Todo-list with a Command to execute each TodoItem
	- Translators: translates an Inbound Event to a Domain Event
	- Dispatchers: takes the produced Outbound Events and dispatches them to the landscape
- Support for the 4 EventModeling feature slice types:
	- State Change: trigger -> Command -> Domain Event(s)
	- State Read: Domain Events -> ReadModel -> endpoint
	- Automation: Domain Events -> Todo-ReadModel -> Command -> Domain Event(s)
	- Translation: Inbound Event -> Command -> Domain Event(s)


