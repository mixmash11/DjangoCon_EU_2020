# Security strategies for multi-tenant applications

**Multitenancy** - multiple customers in one instance (most SaaS products)

## Database-Level Separation
- Requires separate database connections
- Hard to do with django, bad for performance

## Schema Level Separation

### Diagram
- postgres cluster
    - dbs
        - schemas
            -tables
            
Like "name spaces" for tables

### Pros
- clean separation in the database
- possibly allows easy sharding
- very little impact to code base
### Cons
- works only on postgresql
- hard to do cross-tenant queries

django-pgschemas, django-tenant-schemas, others

## Row-Level Separation
every row has a client attached to it

### Pros
- explicit
- flexible
- cross-datable

### Cons
- very easy to get wrong
    - during feature implementation, you won't even spot the bug on the development server
    
### Defense in Depth approach
Multiple layers of security controls

#### First Layer
- Lock it down.
    - Writing all the filter statements
- Beware of magic (for example, django-multitenant)
    - you're not implementing it, easier to make mistakes
- Explicit is better than implicit

#### Second layer
- Scoping (Scope Manager, Scope)
    - FK link explicitly written
    - Scope needs to be active for query (raises error)
    - Scope in with statement
- Still allows multitenant queries
- They implemented a scoping middleware for client-specific views
- Django Scopes
- For forms, use SafeModelChoiceField and override the init
- Safe django shell is djangoscopes compatible (shell-scoped)

Build from the test-suite out

#### Third Layer
- Verify no leaks
- Log queries
- Log result sizes
    - If result size is bigger than biggest client, raise the alarm
- Add honeypots

## QnA
- DB-level is too complicated currently to work with Django
- For testing, they disable and enable the scope as necessary
