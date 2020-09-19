# Understanding Celery to maintain your sanity

## Why Async Task Queue
- Benefits to Decoupling
- Data Processing large tasks
- No waiting for things to happen
- Managing resources
- Parallelizing work

Changing celery settings adds large volume of complexity

## Celery Process
- Client submits a Task to the Task Queue
- Workers execute Tasks from Task Queue

Canvas design?

## Workers
- Workers Spawn subprocesses
- Default is number of processors available
- Workers can be on different machines

## Brokers
- Brokers use a Message Transport to talk with Workers
- Redis is a Broker
- Broker has a value to wait for acknowledgement
    - You can define how long a task waits before retrying

## Something that once went wrong
- Passing contents of file through celery
- Workers prefetch tasks (sometimes a batch of long-running tasks is grabbed even though there are more available
) (run with -O fair)
- Tasks not chaining because of immutable signatures

## Celery CLI

Revoke - revoke doesn't stop the task if its running
Terminate - made for terminating a process
- Could make tasks that are pre-fetched disappear

## QnA
- Profiling is a lot of the work to identify whether to address code or celery
- Tutorials
    - Gotcha Articles

## Links
A good way to hit the ground running
https://www.youtube.com/watch?v=68QWZU_gCDA
https://simpleisbetterthancomplex.com/tutorial/2017/08/20/how-to-use-celery-with-django.html
https://www.revsys.com/tidbits/celery-and-django-and-docker-oh-my/
Common mistakes
https://adamj.eu/tech/2020/02/03/common-celery-issues-on-django-projects/
https://wiredcraft.com/blog/3-gotchas-for-celery/ (hello there TASKS_ACKS_LATE)
https://devchecklists.com/celery-tasks-checklist/