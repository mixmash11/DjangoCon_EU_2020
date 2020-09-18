# Can't Get You Out of my Head

## Task

Read Headers from top 10mil domains (from top 10 mil domain csv list)

## Iterations

### First Run

Read CSV, GET site and insert by row
Read CSV into pandas by chunks, GET site, insert dataset
- 20 requests/min

**Lightbulb Moment**: Only want HTTP Headers, not get method
- 30 requests/min

### Takes way too long
    
**Solution:** Async

CSV wasn't going to work anymore
    - Moved to Atlas (but can use mongodb)
    - Scrapy couldn't handle breath (made for depth)
    - 90 requests per minute
    
### Moving to real async

- Spider (scrapy worker) grabs 2k urls
    - bad intermediate logic for who has requests
    - 350 requests per minute
    - memory leak found
    
### Bugs and Progress
    
- Spiders only run once to prevent memory leak
    - moved to scraping hub (spin up more spiders)
    - 350/min on 6 machines (3 days)
    - found bug (only first doc was marking things as processing)
    
### A way to handle the list of failures

- second worker that identifies failures
    - task queue is only testing **bad** sites
    - task queue only filled with bad urls
