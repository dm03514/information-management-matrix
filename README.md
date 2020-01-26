# Information Management Matrix (IMM)


## Distribute Work Rollouts

IMM tracks progress of work over multiple services (codebases) and/or teams. In multi team projects it's difficult to have a realtime view of project progress.  Consider the simple example of rolling out a library upgrade across 10 services. Many organizations need to do this manually.  IMM helps keep this work visibile by tracking the progress of the rollout and regularly notifiying of progress. 

## Capability Maturity Models

IMM helps keep a pulse on team or service maturity.  It supports defining a maturity model and checking compliance against it.

## Data Model

*Capability*
- id (int): Auto Incrementing ID
- target (string): a service, repo, team, or other entity name
- version (string): supports partiniting up a target. For a service this value could contain a value (**1.5**).  A repo may enter a branch here.
- type (ENUM): version, int, date, etc, string
- value (JSON)
- name: mongo_dependency
- created_time (time):

## Operations
- Current Capabilities: Select value for a group of services

```
1, Service1, v1, semantic_version, v1.3, node-mongo-driver, 2018-01-01
2, Service2, v2, semantic_version, v1.2, node-mongo-driver, 2017-01-01
3, Service2, v2.1, semantic_version, v1.3, node-mongo-driver, 2018-01-01
```

CURR Capability
```
SELECT * from capability where name="node-mongo-driver", GROUP BY (target, version) order by create_time DESC;
```

## API

- /capability - POST - creates a new capability
- 

